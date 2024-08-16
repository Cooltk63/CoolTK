import React, {useEffect, useRef, useState} from "react"
import {Box} from "@mui/system";
import MoreVertIcon from '@mui/icons-material/MoreVert';
import PersonIcon from '@mui/icons-material/Person';
import {
    Avatar,
    Card,
    CardContent,
    Chip,
    DialogTitle,
    Fab,
    Grid,
    IconButton,
    InputBase,
    Menu,
    MenuItem,
    ToggleButton,
    ToggleButtonGroup,
    Typography
} from "@mui/material";
import CardActions from '@mui/material/CardActions';
import axios from "axios";
import SearchIcon from '@mui/icons-material/Search';
import Divider from "@mui/material/Divider";
import Paper from "@mui/material/Paper";
import {Close} from "@mui/icons-material";
import {styled} from '@mui/material/styles';
import VisibilityIcon from "@mui/icons-material/Visibility";
import ModeIcon from "@mui/icons-material/Mode";
import DeleteIcon from "@mui/icons-material/Delete";
import ListItemIcon from "@mui/material/ListItemIcon";
import AddIcon from "@mui/icons-material/Add";
import CreateUser from "./CreateUser";
import AccountBalanceIcon from '@mui/icons-material/AccountBalance'
import DialogContent from "@mui/material/DialogContent";
import Dialog from "@mui/material/Dialog";
import DialogContentText from "@mui/material/DialogContentText";
import DialogActions from "@mui/material/DialogActions";
import Button from "@mui/material/Button";
import Snackbar from "@mui/material/Snackbar";
import {Tooltip} from "@mui/joy";


function stringToColor(string) {
    let hash = 0;
    let i;

    /* eslint-disable no-bitwise */
    for (i = 0; i < string.length; i += 1) {
        hash = string.charCodeAt(i) + ((hash << 5) - hash);
    }

    let color = '#';

    for (i = 0; i < 3; i += 1) {
        const value = (hash >> (i * 8)) & 0xff;
        color += `00${value.toString(16)}`.slice(-2);
    }
    /* eslint-enable no-bitwise */

    return color;
}

function stringAvatar(name) {
    let a = name.split(' ')[0][0];
    let b = name.split(' ')[1][0];
    return {
        sx: {
            bgcolor: stringToColor(name),
        },
        children: `${a + b}`,
    };
}

const CardContainer = styled(Card)(({theme}) => ({
    position: 'relative',
    overflow: 'visible',
    backgroundColor: 'inherit',
    boxShadow: 'none',
    //padding: theme.spacing(2),
}));

const IconButtonWrapper = styled('div')({
    position: 'absolute',
    top: 0,
    right: 0,
    padding: '8px',
});

const AvatarWrapper = styled('div')({
    display: 'flex',
    justifyContent: 'center',
    alignItems: 'center',
    height: '100%',
});

const UserModule = () => {
    document.title = 'CRS | Users';
    const [alignment, setAlignment] = useState('All');
    const [users, setUsers] = useState([]);
    const [searchUser, setSearchUser] = useState('');
    const [branchSearch, setBranchSearch] = useState('');
    const [snackMessage, setSnackMessage] = useState('');
    const [snackOpen, setSnackOpen] = useState(false);
    const [btnClick, setBtnClick] = useState('');
    const [openCreateUser, setOpenCreateUser] = useState(false);
    const [userDetails, setUserDetails] = useState(null);
    const [pfIdForModal, setPfIdForModal] = useState('')
    const [delOpen, setDelOpen] = useState(false);
    const [delUserMsg, setDelUserMsg] = useState('');
    const [pfSearch, setPfSearch] = useState('');
    const [anchorEl, setAnchorEl] = React.useState(null);
    const [roleFilteredList, setRoleFilteredList] = useState([]);
    const open = Boolean(anchorEl);


    useEffect(() => {
        loadUsers().then(r => {
            console.log('data fetched.');
        });
    }, [])

    const handleChange = (event, newAlignment) => {
        setAlignment(newAlignment);
    };

    const handleClickOpenCreateUser = () => {
        setOpenCreateUser(true);
        setBtnClick('create');
    };

    const handleFabClose = () => {
        setOpenCreateUser(false);
    };

    const loadUsers = async () => {
        try {
            const response =
                await axios.post("Server/userModule/getList", {},
                    {
                        headers: {
                            'Authorization': `Bearer ${localStorage.getItem('token')}`,
                        }
                    });
            console.log(response);
            setUsers(response.data.result)
            setRoleFilteredList(users)
        } catch (e) {
            console.error(e)
        }
    }

    let filter
    if (roleFilteredList.length === 0) {
        filter = users.map((row, index) => ({
            ...row,
            originalIndex: index
        })).filter(row =>
            row.FIRST_NAME.toLowerCase().includes(searchUser.toLowerCase()) ||
            row.LAST_NAME.toLowerCase().includes(searchUser.toLowerCase()) ||
            row.PF_NUMBER.toString().includes(searchUser.toString())
        );
    } else {
        filter = roleFilteredList.map((row, index) => ({
            ...row,
            originalIndex: index
        })).filter(row =>
            row.FIRST_NAME.toLowerCase().includes(searchUser.toLowerCase()) ||
            row.LAST_NAME.toLowerCase().includes(searchUser.toLowerCase()) ||
            row.PF_NUMBER.toString().includes(searchUser.toString())
        );
    }


    const handleSearchBranchChange = (e) => {
        setSearchUser(e.target.value);
    }

    const getUserListByBranch = async () => {
        if (branchSearch) {
            console.log("branch search 183..:"+branchSearch);
            try {
                const response = await axios.post('/Server/userModule/getUserBranch',
                    {
                        branch: branchSearch
                    }, {
                        headers: {
                            'Authorization': `Bearer ${localStorage.getItem('token')}`,
                        }
                    });
                if (response.data.result.length !== 0) {
                    setUsers(response.data.result)
                } else {
                    setSnackOpen(true);
                    setSnackMessage('No user found for branch ' + branchSearch);
                }
            } catch (e) {
                console.error(e);
            }
        } else {
            setSnackOpen(true);
            setSnackMessage('Enter branch code to search');
        }
    }

    const handleSearchBranchClear = (e) => {
        setSearchUser('');
    }

    const handleSearchByPf = async () => {
        if (pfSearch !== '') {
            console.log("pfsearch"+ pfSearch);
            try {
                const response = await axios.post('Server/userModule/searchUserByPf',
                    {
                        pfNumber: pfSearch
                    }, {
                        headers: {
                            'Authorization': `Bearer ${localStorage.getItem('token')}`,
                        }
                    });
                if (response.data.message === 'User already exists') {
                    let singleUser = [response.data.result];
                    setUsers(singleUser)
                } else {
                    setSnackOpen(true);
                    setSnackMessage('No user found')
                }
            } catch (e) {
                console.error(e)
            }
        } else {
            setSnackOpen(true);
            setSnackMessage('Enter PF Number to search');
        }

    }

    const handleRoleFilter = (role) => {
        if (role === '00') {
            setRoleFilteredList(users);
        } else {
            let filteredRow = users.filter(f => (f.USER_ROLE === role));
            setRoleFilteredList(filteredRow);
        }

    }

    const handleClick = (e, value) => {
        setAnchorEl(e.currentTarget);
        setPfIdForModal(value)
    };

    const handleClose = (data) => {
        setAnchorEl(null);
    };

    const handleMenuAction = (data) => {
        let map = users.filter(f => f.PF_NUMBER === pfIdForModal);
        setAnchorEl(null);
        setOpenCreateUser(true);
        setUserDetails(map[0]);
        setBtnClick(data);
    }

    const handleDeleteAction = async (data) => {
        let map = users.filter(f => f.PF_NUMBER === pfIdForModal);
        console.log(map)
        setDelOpen(true);
        setDelUserMsg('Are you sure to delete ' + map[0].FIRST_NAME + ' ' + map[0].LAST_NAME + ' ?');
    }

    const handleConfirmDelete = () => {
        try {
            const response = axios.post('/Server/userModule/deleteUser',
                {
                    pfNumber: pfIdForModal
                }, {
                    headers: {
                        'Authorization': `Bearer ${localStorage.getItem('token')}`,
                    }
                });
            console.log(response.data);
            setDelOpen(false)
        } catch (e) {
            console.error(e)
        }
    }


    return (
        <Box sx={{display: 'flex', flexDirection: 'column'}}>
            <Grid container>
                <Typography variant={'h5'}>
                    User Module
                </Typography>
            </Grid>

            <Grid container spacing={2}>
                <Box sx={{
                    display: 'flex',
                    width: '100%',
                    //flexDirection: 'row',
                    alignItems: 'center',
                    justifyContent: 'center',
                    gap: 1,

                }}>
                    <Paper
                        style={{textAlign: 'center', width: '25%'}}
                           component="form"
                           sx={{
                               p: '2px 4px',
                               display: 'flex',
                               alignItems: 'center',
                               width: "25%"
                           }}>
                        <AccountBalanceIcon sx={{ml: 1}}/>
                        <InputBase  autoFocus
                            sx={{ml: 1, flex: 1}} placeholder="Search Branch"
                                   inputProps={{
                                       'aria-label': 'search google maps',
                                       maxLength: 5
                                   }}
                                   value={branchSearch}
                                   onChange={(e) => {
                                       if (/^\d*$/.test(e.target.value)) {
                                           setBranchSearch(e.target.value);
                                       }
                                   }}
                        />
                       <Divider sx={{height: 28, m: 1.0}} orientation="vertical"/>

                        <IconButton type="button" sx={{p: '10px'}} aria-label="clear"
                                    onClick={getUserListByBranch}>
                            <SearchIcon/>
                        </IconButton>
                    </Paper>
                   {/* <Divider sx={{height: 28, m: 1.0}} orientation="vertical"/>*/}
                    &emsp;
                    <Paper
                        style={{textAlign: 'center', width: '25%'}}
                           component="form"
                           sx={{
                               p: '2px 4px',
                               display: 'flex',
                               alignItems: 'center',
                               width: "25%"
                           }}
                    >
                        <PersonIcon sx={{ml: 1}}/>
                        <InputBase sx={{ml: 1, flex: 1}}
                                   placeholder="Search PF Number "
                                   inputProps={{
                                       'aria-label': 'search user by pfId',
                                       maxLength: 7
                                   }}
                                   value={pfSearch}
                                   onChange={(e) => {
                                       if (/^\d*$/.test(e.target.value)) {
                                           setPfSearch(e.target.value)
                                       }
                                   }}

                        />
                        <Divider sx={{height: 28, m: 1.0}} orientation="vertical"/>
                        <IconButton type="button" sx={{p: '10px'}} aria-label="clear"
                                    onChange={handleSearchByPf}>
                            <SearchIcon onClick={handleSearchByPf}/>
                        </IconButton>
                    </Paper>
                </Box>
            </Grid>
            <br/>
            <Grid container spacing={0} sx={{alignItems: 'center'}}>
                <Grid item xs={1}>
                    <Typography variant={'h6'}>
                        Filter By Role:
                    </Typography>
                </Grid>
                <Grid item xs={8} sx={{justifyContent: 'center', alignItems: 'center'}}>
                    <Box>
                        <ToggleButtonGroup
                            color="primary"
                            value={alignment}
                            exclusive
                            onChange={handleChange}
                            aria-label="Platform">
                            <ToggleButton onClick={() => handleRoleFilter('00')} value="All">All</ToggleButton>
                            <ToggleButton onClick={() => handleRoleFilter('Maker')} value="Maker">Maker</ToggleButton>
                            <ToggleButton onClick={() => handleRoleFilter('Checker')}
                                          value="Checker">Checker</ToggleButton>
                            <ToggleButton onClick={() => handleRoleFilter('Auditor')}
                                          value="Auditor">Auditor</ToggleButton>
                            <ToggleButton onClick={() => handleRoleFilter('RO Manager')} value="RO Manager">RO
                                Manager</ToggleButton>
                            <ToggleButton onClick={() => handleRoleFilter('LHO Manager')} value="LHO Manager">LHO
                                Manager</ToggleButton>
                        </ToggleButtonGroup>
                    </Box>
                </Grid>

                <Grid item xs={3}>
                    <Paper style={{textAlign: 'center', width: '100%'}}
                           component="form"
                           sx={{
                               p: '2px 4px',
                               display: 'flex',
                               alignItems: 'center',
                               width: 350,

                           }}
                    >
                        <SearchIcon sx={{ml: 1}}/>
                        <Divider sx={{height: 28, m: 1.0}} orientation="vertical"/>
                        <InputBase sx={{ml: 1, flex: 1}}
                                   placeholder=" Filter by Branch OR User "
                                   inputProps={{'aria-label': 'search branch or user'}}
                                   value={searchUser}
                                   onChange={handleSearchBranchChange}
                        />
                        <Divider sx={{height: 28, m: 1.0}} orientation="vertical"/>
                        <IconButton type="button" sx={{p: '10px'}} aria-label="clear"
                                    onClick={handleSearchBranchClear}
                        >
                            <Close/>
                        </IconButton>
                    </Paper>
                </Grid>
            </Grid>
            <br/>
            <Divider/>
            <Box sx={{height: '70vh', overflow: 'auto', mt:1}}>
                <Grid container spacing={2} direction='row'>
                    {filter ? (<></>) : (<p>No Users Found</p>)}
                    {filter.map((vd, index) =>
                        <Grid item key={vd.PF_NUMBER}>
                            <Card sx={{width: 280, height: 240}}>
                                <CardContent sx={{textAlign: 'center'}}>
                                    <CardContainer>
                                        <IconButtonWrapper>
                                            <IconButton value={vd.PF_NUMBER}
                                                        aria-label="settings"
                                                        onClick={(e) => handleClick(e, vd.PF_NUMBER)}
                                                        aria-controls={open ? 'basic-menu' : undefined}
                                                        aria-haspopup="true"
                                                        aria-expanded={open ? 'true' : undefined}>
                                                <MoreVertIcon/>
                                            </IconButton>
                                        </IconButtonWrapper>
                                        <CardContent>
                                            <AvatarWrapper>
                                                <Avatar variant="Large"
                                                    sx={{
                                                        alignItems: 'center',
                                                        width: 100,
                                                        height: 100,
                                                        mt: 2,
                                                        textAlign: 'center'
                                                    }}
                                                    {...stringAvatar(vd.FIRST_NAME.charAt(0).toUpperCase() + ' '
                                                        + vd.LAST_NAME.charAt(0).toUpperCase())
                                                    }
                                                />
                                            </AvatarWrapper>
                                        </CardContent>
                                    </CardContainer>
                                    <Menu
                                        anchorEl={anchorEl}
                                        id="account-menu"
                                        open={open}
                                        onClose={handleClose}
                                        transformOrigin={{horizontal: 'right', vertical: 'top'}}
                                        anchorOrigin={{horizontal: 'right', vertical: 'bottom'}}
                                    >
                                        <MenuItem onClick={(e) => handleMenuAction('view')}>
                                            <ListItemIcon>
                                                <VisibilityIcon fontSize="small"/>
                                            </ListItemIcon>
                                            View User
                                        </MenuItem>
                                        <Divider/>
                                        <MenuItem onClick={(e) => handleMenuAction('edit')}>
                                            <ListItemIcon>
                                                <ModeIcon fontSize="small"/>
                                            </ListItemIcon>
                                            Edit User
                                        </MenuItem>
                                        <Divider/>
                                        <MenuItem onClick={(e) => handleDeleteAction('delete')}>
                                            <ListItemIcon>
                                                <DeleteIcon fontSize="small"/>
                                            </ListItemIcon>
                                            Delete User
                                        </MenuItem>
                                    </Menu>

                                    <Typography variant="body1" color="text.secondary">
                                        {vd.PF_NUMBER}
                                    </Typography>
                                    <Tooltip title={`${vd.FIRST_NAME},${vd.LAST_NAME}`}>
                                    <Typography noWrap sx={{
                                        overflow:'hidden',textOverflow:'ellipsis',maxWidth:'120px'
                                    }}
                                        gutterBottom variant="body1"    style={{fontWeight:600}}>
                                        {/*{vd.FIRST_NAME} {vd.LAST_NAME}*/}
                                        {(vd.FIRST_NAME +''+vd.LAST_NAME).slice(0,12)}
                                    </Typography>
                                    </Tooltip>
                                    <Typography variant="body2" color="text.secondary">
                                      Branch - {vd.BRANCH_CODE}
                                    </Typography>
                                </CardContent>
                                <CardActions sx={{alignItems: 'center', justifyContent: 'center'}}>
                                    <Chip style={{width: "auto", height: 30, alignItems: 'center'}}
                                          label={vd.USER_ROLE === null ? "Role" : vd.USER_ROLE}
                                          sx={
                                              vd.USER_ROLE === "Maker" ? {
                                                      backgroundColor: '#f60a36',
                                                      color: 'white',
                                                      fontSize: 16
                                                  } :
                                                  vd.USER_ROLE === "Checker" ? {
                                                          backgroundColor: '#f65905',
                                                          color: 'white',
                                                          fontSize: 16
                                                      }
                                                      : vd.USER_ROLE === "Auditor" ? {
                                                              backgroundColor: '#0becd9',
                                                              color: 'white',
                                                              fontSize: 16
                                                          }
                                                          : vd.USER_ROLE === "RO" ? {
                                                                  backgroundColor: '#0becd9',
                                                                  color: 'white',
                                                                  fontSize: 16
                                                              }
                                                              : vd.USER_ROLE === "LHO Manager" ? {
                                                                      backgroundColor: '#008080',
                                                                      color: 'white',
                                                                      fontSize: 16
                                                                  }
                                                                  : {
                                                                      backgroundColor: '#5c1a03',
                                                                      color: 'white',
                                                                      fontSize: 16
                                                                  }}/>
                                </CardActions>
                            </Card>
                        </Grid>
                    )}

                </Grid>
                <Fab onClick={handleClickOpenCreateUser}
                     color="primary"
                     variant="extended" sx={{
                    position: "fixed",
                    borderRadius: 1,
                    fontSize: '15px',
                    bottom: (theme) => theme.spacing(10),
                    right: (theme) => theme.spacing(10)
                }}>
                    <AddIcon sx={{mr: 1}}/>
                    Creat User
                </Fab>
            </Box>
            <CreateUser openCreateUser={openCreateUser} handleFab={handleFabClose} userDetails={userDetails}
                        btnClick={btnClick}/>
            <Dialog
                open={delOpen}
                onClose={() => setDelOpen(false)}
                maxWidth={"md"}
                aria-labelledby="alert-dialog-title"
                aria-describedby="alert-dialog-description"
            >
                <DialogTitle id="alert-dialog-title">
                    {"Delete User"}
                </DialogTitle>
                <DialogContent>
                    <DialogContentText id="alert-dialog-description">
                        {delUserMsg}
                    </DialogContentText>
                </DialogContent>
                <DialogActions>
                    <Button onClick={() => setDelOpen(false)}>Confirm</Button>
                    <Button onClick={() => handleConfirmDelete()} autoFocus>
                        Cancel
                    </Button>
                </DialogActions>
            </Dialog>
            <Snackbar
                open={snackOpen}
                anchorOrigin={{vertical: 'top', horizontal: 'center'}}
                autoHideDuration={3000}
                onClose={() => setSnackOpen(false)}
                message={snackMessage}
            />
        </Box>
    )
}
export default UserModule

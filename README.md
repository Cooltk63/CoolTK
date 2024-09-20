app.controller('annex2CCircleReportController', function ($scope, $rootScope, $http, $window, $sessionStorage,
                                                          $state, $timeout, $location, Idle, Keepalive, $modal,
                                                          ModalService, userFactory, annex2CFactory, refreshFactory, AES256) {


    var annex2C = this;
    $scope.started = false;
    $scope.sessionUser = JSON.parse(AES256.decrypt($rootScope.globals.currentUser));
    let reportID="5002"
    annex2C.btnFlag='N';
    let circleCode =$scope.sessionUser.circleCode;
    console.log("ANNEX2C Controller QED IS:" +$scope.sessionUser.quarterEndDate);
    console.log("ANNEX2C Controller CircleCode IS:" +circleCode);

    // List for SFTP Fn.
    annex2C.CirclesList = ["001", "002", "003", "004", "005","006","007","008","009","011","015","014","016","017","010","012","013","023","024","027"];

    // Function to check if a 3-digit circleCode (as a string) exists in the list
    annex2C.isCircleInList = function(circleCode) {
        return annex2C.CirclesList.includes(circleCode);
    };


    // Get Screen Data Main Fn.
    annex2C.getScreenData=function() {

        // Parameters Required for SFTP
        const sftpParams = {
            'circleCode': $scope.sessionUser.circleCode,
            'qed': $scope.sessionUser.quarterEndDate,
            'reportID': reportID,
            'reportName': 'ANX2C'
        };

        // Checked if Circle Authorized to Fetch Files/Data
        if (annex2C.isCircleInList(circleCode)) {

            console.log(circleCode + " exists in the list.");

            // Call SFTP Here
            annex2CFactory.getSFTPAnnex2CData(sftpParams).then(function (data) {
                    console.log("Received data getSFTPAnnex2CData Load :" + JSON.stringify(data));
                    alert("Inside getSFTPAnnex2CData Response Data!!" + data);

                    annex2C.disabledAdvancesFields=true;
                    // SFTP Successfully Inserted Data
                    if (data) {
                        // Show the Success Model
                        annex2C.displayModel(data);
                        annex2C.getSavedData();
                    }

                    // Error Or File Mismatch IN Files SFTP
                    else {
                        // Show the Error Model & Redirected back to worklist
                        annex2C.displayModel(data);
                        alert("Error While SFTP Data...!")
                    }
                },

                function (errResponse) {
                    console.error('Error while getting Files from SFTP ');
                });


        } else {
            alert("Circle not Exists in List All data feeds Manually")

            // Calling getData For Manually Inserting Values
            annex2C.getSavedData();
            annex2C.disabledAdvancesFields=false;

            console.log(circleCode + " does not exist in the list.");
        }
    }
    // Get Screen Data Fn. END Here


    // Parse Float Fn
    annex2C.parseFloat = function (value) {
        if (isNaN(value)) {
            value = 0.00;
        }
        return parseFloat(value * 1);
    }


    // Getting Data from Backend to Screen
    annex2C.getSavedData = function (){

        var params = {
            'circleCode': $scope.sessionUser.circleCode,
            'qed': $scope.sessionUser.quarterEndDate,
            'reportID': '5002',
            'userId': $scope.sessionUser.userId,

        }
        annex2CFactory.getSavedDataAnnex2C(params).then(function (data) {
                //       alert("Inside getSavedDataAnnex2C !!" +data);
                console.log("Received data on Load :" + JSON.stringify(data));
                annex2C.row = data;
            },
            function(errResponse)
            {
                console.error('Error while getting params');
            });
    };
    // Ended get Data Fn.

    // -->>> WatchCollection Calculations
    $scope.$watchCollection('annex2C.row',function (newValue ,oldValue) {

        annex2C.row.generalSUM = (annex2C.parseFloat(annex2C.row.general * annex2C.row.generalMUL) / 10000).toFixed(2);

        annex2C.row.personalLoanNBFCNDSL1SUM= (annex2C.parseFloat(annex2C.row.personalLoanNBFCNDSL * annex2C.row.personalLoanNBFCNDSLMUL) /10000).toFixed(2);

        annex2C.row.exposureCapMkt1SUM= (annex2C.parseFloat(annex2C.row.exposureCapMkt * annex2C.row.exposureCapMktMUL) /10000).toFixed(2);

        annex2C.row.standard1SUM= (annex2C.parseFloat(annex2C.row.standard * annex2C.row.standardMUL) /100).toFixed(2);

        annex2C.row.npaUpgradedStdAsset1SUM= (annex2C.parseFloat((annex2C.row.npaUpgradedStdAsset) * annex2C.row.npaUpgradedStdAssetMUL) /100).toFixed(2);

        annex2C.row.newRestructuredStdACS1SUM= (annex2C.parseFloat((annex2C.row.newRestructuredStdACS) * annex2C.row.newRestructuredStdACSMUL) /100).toFixed(2);

        annex2C.row.memeRestStdAssets1SUM= (annex2C.parseFloat((annex2C.row.memeRestStdAssets) * annex2C.row.memeRestStdAssetsMUL) /100).toFixed(2);

        annex2C.row.covid1SUM= (annex2C.parseFloat(annex2C.row.covid * annex2C.row.covidMUL)/100).toFixed(2);

        annex2C.row.commercialRealEstResdhousing1SUM= (annex2C.parseFloat(annex2C.row.commercialRealEstResdhousing * annex2C.row.commercialRealEstResdhousingMUL) /10000).toFixed(2);

        annex2C.row.expCommRealEst1SUM= (annex2C.parseFloat(annex2C.row.expCommRealEst * annex2C.row.expCommRealEstMUL) /100).toFixed(2);

        annex2C.row.others1SUM= (annex2C.parseFloat(annex2C.row.others * annex2C.row.othersMUL) /10000).toFixed(2);

        // New Columns Data Here
        annex2C.row.wilFul1SUM= (annex2C.parseFloat(annex2C.row.wilFul * annex2C.row.wilFulMUL)/100).toFixed(2);
        annex2C.row.secured1SUM= (annex2C.parseFloat(annex2C.row.secured * annex2C.row.securedMUL)/100).toFixed(2);
        annex2C.row.unSecured1SUM= (annex2C.parseFloat(annex2C.row.unSecured * annex2C.row.unSecuredMUL)/100).toFixed(2);
        annex2C.row.restructure1SUM= (annex2C.parseFloat(annex2C.row.restructure * annex2C.row.restructureMUL)/100).toFixed(2);
        annex2C.row.nonRestructure1SUM= (annex2C.parseFloat(annex2C.row.nonRestructure * annex2C.row.nonRestructureMUL)/10000).toFixed(2);
        // New Columns Data Here
        annex2C.row.allOthers1SUM= (annex2C.parseFloat(annex2C.row.allOthers * annex2C.row.allOthersMUL) /10000).toFixed(2);

        //Total SUM for Advances

        annex2C.row.total = (annex2C.parseFloat(annex2C.row.general)
            + annex2C.parseFloat(annex2C.row.personalLoanNBFCNDSL)
            + annex2C.parseFloat(annex2C.row.exposureCapMkt)
            + annex2C.parseFloat(annex2C.row.standard)
            + annex2C.parseFloat(annex2C.row.npaUpgradedStdAsset)
            + annex2C.parseFloat(annex2C.row.newRestructuredStdACS)
            + annex2C.parseFloat(annex2C.row.memeRestStdAssets)
            + annex2C.parseFloat(annex2C.row.covid)
            + annex2C.parseFloat(annex2C.row.commercialRealEstResdhousing)
            + annex2C.parseFloat(annex2C.row.expCommRealEst)
            + annex2C.parseFloat(annex2C.row.others)
            /* ><><>New Columns Addition Here*/
            + annex2C.parseFloat(annex2C.row.wilFul)
            + annex2C.parseFloat(annex2C.row.secured)
            + annex2C.parseFloat(annex2C.row.unSecured)
            + annex2C.parseFloat(annex2C.row.restructure)
            + annex2C.parseFloat(annex2C.row.nonRestructure)
            /*New Columns Addition Here*/
            + annex2C.parseFloat(annex2C.row.allOthers)).toFixed(2);


        // Total SUM for Provisions
        annex2C.row.totalSUM= (annex2C.parseFloat(annex2C.row.generalSUM)
            +annex2C.parseFloat(annex2C.row.personalLoanNBFCNDSL1SUM)
            +annex2C.parseFloat(annex2C.row.exposureCapMkt1SUM)
            +annex2C.parseFloat(annex2C.row.standard1SUM)
            +annex2C.parseFloat(annex2C.row.npaUpgradedStdAsset1SUM)
            +annex2C.parseFloat(annex2C.row.newRestructuredStdACS1SUM)
            +annex2C.parseFloat(annex2C.row.memeRestStdAssets1SUM)
            +annex2C.parseFloat(annex2C.row.covid1SUM)
            +annex2C.parseFloat(annex2C.row.commercialRealEstResdhousing1SUM)
            +annex2C.parseFloat(annex2C.row.expCommRealEst1SUM)
            +annex2C.parseFloat(annex2C.row.others1SUM)
            /*New Columns Addition Here*/
            + annex2C.parseFloat(annex2C.row.wilFul1SUM)
            + annex2C.parseFloat(annex2C.row.secured1SUM)
            + annex2C.parseFloat(annex2C.row.unSecured1SUM)
            + annex2C.parseFloat(annex2C.row.restructure1SUM)
            + annex2C.parseFloat(annex2C.row.nonRestructure1SUM)
            /*New Columns Addition Here*/
            +annex2C.parseFloat(annex2C.row.allOthers1SUM)).toFixed(2);

    });


    // -->>> Save Data Fn.
    annex2C.saveData=function(row)
    {

        var params = {
            'circleCode': $scope.sessionUser.circleCode,
            'qed': $scope.sessionUser.quarterEndDate,
            'reportID': '5002',

            // Advances
            // 'general': annex2C.parseFloat(annex2C.row.general),
            'general': annex2C.row.general,
            'personalLoanNBFCNDSL':annex2C.row.personalLoanNBFCNDSL,
            'exposureCapMkt':annex2C.row.exposureCapMkt,
            'standard':annex2C.row.standard,
            'npaUpgradedStdAsset':annex2C.row.npaUpgradedStdAsset,
            'newRestructuredStdACS':annex2C.row.newRestructuredStdACS,
            'memeRestStdAssets':annex2C.row.memeRestStdAssets,
            'covid':annex2C.row.covid,
            'commercialRealEstResdhousing':annex2C.row.commercialRealEstResdhousing,
            'expCommRealEst':annex2C.row.expCommRealEst,
            'others':annex2C.row.others,
            // New Columns Data Here
            'wilFul':annex2C.row.wilFul,
            'secured':annex2C.row.secured,
            'unSecured':annex2C.row.unSecured,
            'restructure':annex2C.row.restructure,
            'nonRestructure':annex2C.row.nonRestructure,
            // New Columns Data Here
            'allOthers':annex2C.row.allOthers,
            'total':annex2C.row.total,

            //Provisions
            'general1SUM':annex2C.row.generalSUM,
            'personalLoanNBFCNDSL1SUM':annex2C.row.personalLoanNBFCNDSL1SUM,
            'exposureCapMkt1SUM':annex2C.row.exposureCapMkt1SUM,
            'standard1SUM':annex2C.row.standard1SUM,
            'npaUpgradedStdAsset1SUM':annex2C.row.npaUpgradedStdAsset1SUM,
            'newRestructuredStdACS1SUM':annex2C.row.newRestructuredStdACS1SUM,
            'memeRestStdAssets1SUM':annex2C.row.memeRestStdAssets1SUM,
            'covid1SUM':annex2C.row.covid1SUM,
            'commercialRealEstResdhousing1SUM':annex2C.row.commercialRealEstResdhousing1SUM,
            'expCommRealEst1SUM':annex2C.row.expCommRealEst1SUM,
            'others1SUM':annex2C.row.others1SUM,
            // New Columns Data Here
            'wilFul1SUM':annex2C.row.wilFul1SUM,
            'secured1SUM':annex2C.row.secured1SUM,
            'unSecured1SUM':annex2C.row.unSecured1SUM,
            'restructure1SUM':annex2C.row.restructure1SUM,
            'nonRestructure1SUM':annex2C.row.nonRestructure1SUM,
            // New Columns Data Here
            'allOthers1SUM':annex2C.row.allOthers1SUM,
            'totalSUM':annex2C.row.totalSUM,

        }

        annex2CFactory.saveData(params).then(function (data) {
                if (data) {
                    console.log("saveData result is :"+data);
                    annex2C.displayMessage = "Report Saved Successfully";

                    /////////////
                    $('#saveData')
                        .modal(
                            {
                                backdrop: 'static',
                                keyboard: false,
                                modal: true
                            });
                    $('#saveData')
                        .on(
                            'shown.bs.modal',
                            function () {
                                $(
                                    '#saveData')
                                    .trigger(
                                        'focus');
                            });
                    /////////////

                } else {
                    ///
                    annex2C.displayMessage = "Report Not Saved ";
                    /////////////
                    $('#failedSaveSubmit')
                        .modal(
                            {
                                backdrop: 'static',
                                keyboard: false,
                                modal: true
                            });
                    $('#failedSaveSubmit')
                        .on('shown.bs.modal',
                            function () {
                                $('#failedSaveSubmit')
                                    .trigger('focus');
                            });
                }
            },
            function (errResponse) {
                console.error('Error while Saving params');
            });

    }
    // Ended Save Data Fn.


    // -->>> Reset Data Fn.
    annex2C.resetData=function ()
    {
        annex2C.row.general = "0.00";
        annex2C.row.personalLoanNBFCNDSL = "0.00";
        annex2C.row.exposureCapMkt = "0.00";
        annex2C.row.standard = "0.00";
        annex2C.row.npaUpgradedStdAsset = "0.00";
        annex2C.row.newRestructuredStdACS = "0.00";
        annex2C.row.memeRestStdAssets = "0.00";
        annex2C.row.covid = "0.00";
        annex2C.row.commercialRealEstResdhousing = "0.00";
        annex2C.row.expCommRealEst = "0.00";
        annex2C.row.others = "0.00";
        // New Columns Data Here
        annex2C.row.wilFul="0.00";
        annex2C.row.secured="0.00";
        annex2C.row.unSecured="0.00";
        annex2C.row.restructure="0.00";
        annex2C.row.nonRestructure="0.00";
        // New Columns Data Here
        annex2C.row.allOthers = "0.00";

    }
    // Ended resetData Fn.

    // -->>> Submit Data Fn.
    annex2C.submitData=function(row)
    {
        /*console.log("Inside Submit miscRMLId : "+miscRMLId);
        console.log("Inside Submit miscflag : "+miscflag);
        console.log("Inside Submit miscstatus : "+miscstatus);*/

        var params = {
            'circleCode': $scope.sessionUser.circleCode,
            'qed': $scope.sessionUser.quarterEndDate,
            'reportID': '5002',

            // Advances
            'general': annex2C.row.general,
            'personalLoanNBFCNDSL': annex2C.row.personalLoanNBFCNDSL,
            'exposureCapMkt': annex2C.row.exposureCapMkt,
            'standard': annex2C.row.standard,
            'npaUpgradedStdAsset': annex2C.row.npaUpgradedStdAsset,
            'newRestructuredStdACS': annex2C.row.newRestructuredStdACS,
            'memeRestStdAssets': annex2C.row.memeRestStdAssets,
            'covid': annex2C.row.covid,
            'commercialRealEstResdhousing': annex2C.row.commercialRealEstResdhousing,
            'expCommRealEst': annex2C.row.expCommRealEst,
            'others': annex2C.row.others,
            // New Columns Data Here
            'wilFul1':annex2C.row.wilFul,
            'secured1':annex2C.row.secured,
            'unSecured1':annex2C.row.unSecured,
            'restructure1':annex2C.row.restructure,
            'nonRestructure1':annex2C.row.nonRestructure,
            // New Columns Data Here
            'allOthers': annex2C.row.allOthers,
            'total':annex2C.row.total,


            //Provisions
            'general1SUM': annex2C.row.generalSUM,
            'personalLoanNBFCNDSL1SUM':annex2C.row.personalLoanNBFCNDSL1SUM,
            'exposureCapMkt1SUM': annex2C.row.exposureCapMkt1SUM,
            'standard1SUM': annex2C.row.standard1SUM,
            'npaUpgradedStdAsset1SUM': annex2C.row.npaUpgradedStdAsset1SUM,
            'newRestructuredStdACS1SUM': annex2C.row.newRestructuredStdACS1SUM,
            'memeRestStdAssets1SUM': annex2C.row.memeRestStdAssets1SUM,
            'covid1SUM': annex2C.row.covid1SUM,
            'commercialRealEstResdhousing1SUM': annex2C.row.commercialRealEstResdhousing1SUM,
            'expCommRealEst1SUM':annex2C.row.expCommRealEst1SUM,
            'others1SUM': annex2C.row.others1SUM,
            // New Columns Data Here
            'wilFul1SUM':annex2C.row.wilFul1SUM,
            'secured1SUM':annex2C.row.secured1SUM,
            'unSecured1SUM':annex2C.row.unSecured1SUM,
            'restructure1SUM':annex2C.row.restructure1SUM,
            'nonRestructure1SUM':annex2C.row.nonRestructure1SUM,
            // New Columns Data Here
            'allOthers1SUM': annex2C.row.allOthers1SUM,
            'totalSUM': annex2C.row.totalSUM,

        }

        annex2CFactory.submitData(params).then(function (data) {
                if (data) {
                    console.log("Value of Data is: "+data);
                    annex2C.displayMessage = "Report Submitted Successfully";
                    /////////////
                    $('#submitData')
                        .modal(
                            {
                                backdrop: 'static',
                                keyboard: false,
                                modal: true
                            });
                    $('#submitData')
                        .on('shown.bs.modal',
                            function () {
                                $('#submitData')
                                    .trigger('focus');
                            });
                }
                else {

                    ///
                    annex2C.displayMessage = "Report Not Submitted ";
                    /////////////
                    $('#failedSaveSubmit')
                        .modal(
                            {
                                backdrop: 'static',
                                keyboard: false,
                                modal: true
                            });
                    $('#failedSaveSubmit')
                        .on('shown.bs.modal',
                            function () {
                                $('#failedSaveSubmit')
                                    .trigger('focus');
                            });

                    ///

                    // alert("Failed to save Data");
                }
            },
            function (errResponse) {
                console.error('Error while Saving params');
            });

    }


    // -->>> Validate the user Input ----->
    annex2C.checkNumber=function(numVal, numId)
    {
        console.log("into check num fn   " + numVal);
        console.log("into check num numId    " + numId);

        var val = document.getElementById(numId).value;
        console.log("val- "+val);

        if (val.match(/\s/g)) {
            alert("Space is not allowed");
            // document.getElementById(numId).value = "0.00";


            if (numVal == "annex2C.row.general") {
                annex2C.row.general = "0.00";
                annex2C.row.generalSUM = "0.00";
            }
            else if (numVal == "annex2C.row.personalLoanNBFCNDSL") {
                annex2C.row.personalLoanNBFCNDSL ="0.00";
                annex2C.row.personalLoanNBFCNDSL1SUM = "0.00";
            }
            else  if (numVal == "annex2C.row.exposureCapMkt") {
                annex2C.row.exposureCapMkt = "0.00";
                annex2C.row.exposureCapMkt1SUM = "0.00";
            }
            else if (numVal == "annex2C.row.standard") {
                annex2C.row.standard = "0.00";
                annex2C.row.standard1SUM = "0.00";
            }
            else if (numVal == "annex2C.row.npaUpgradedStdAsset") {
                annex2C.row.npaUpgradedStdAsset = "0.00";
                annex2C.row.npaUpgradedStdAsset1SUM = "0.00";
            }
            else if (numVal == "annex2C.row.newRestructuredStdACS") {
                annex2C.row.newRestructuredStdACS = "0.00";
                annex2C.row.newRestructuredStdACS1SUM = "0.00";
            }
            else if (numVal == "annex2C.row.memeRestStdAssets") {
                annex2C.row.memeRestStdAssets = "0.00";
                annex2C.row.memeRestStdAssets1SUM = "0.00";
            }
            else if (numVal == "annex2C.row.covid") {
                annex2C.row.covid = "0.00";
                annex2C.row.covid1SUM = "0.00";
            }
            else if (numVal == "annex2C.row.commercialRealEstResdhousing") {
                annex2C.row.commercialRealEstResdhousing = "0.00";
                annex2C.row.commercialRealEstResdhousing1SUM = "0.00";
            }
            else if (numVal == "annex2C.row.expCommRealEst") {
                annex2C.row.expCommRealEst = "0.00";
                annex2C.row.expCommRealEst1SUM = "0.00";
            }
            else if (numVal == "annex2C.row.others") {
                annex2C.row.others = "0.00";
                annex2C.row.others1SUM = "0.00";
            }

            // New Columns Data Here
            else if (numVal == "annex2C.row.wilFul") {
                annex2C.row.wilFul = "0.00";
                annex2C.row.wilFul1SUM = "0.00";
            }else if (numVal == "annex2C.row.secured") {
                annex2C.row.secured = "0.00";
                annex2C.row.secured1SUM = "0.00";
            }else if (numVal == "annex2C.row.unSecured") {
                annex2C.row.unSecured = "0.00";
                annex2C.row.unSecured1SUM = "0.00";
            }else if (numVal == "annex2C.row.restructure") {
                annex2C.row.restructure = "0.00";
                annex2C.row.restructure1SUM = "0.00";
            }else if (numVal == "annex2C.row.nonRestructure") {
                annex2C.row.nonRestructure = "0.00";
                annex2C.row.nonRestructure1SUM = "0.00";
            }
            // New Columns Data Here

            else if (numVal == "annex2C.row.allOthers") {
                annex2C.row.allOthers = "0.00";
                annex2C.row.allOthers1SUM = "0.00";
            }
            else if (numVal == "annex2C.row.total") {
                annex2C.row.total = "0.00";
                annex2C.row.totalSUM = "0.00";
            }
            console.log("Value of Field After Setting Value: "+document.getElementById(numId).value)
            return false;
        }

        var pattern= /-0\.\d{2}$/;
        if (val.match(pattern)) {
            alert("Please enter Valid Amount");
            // document.getElementById(numId).value = "0.00";
            /////
            if (numVal == "annex2C.row.general") {
                annex2C.row.general = "0.00";
                annex2C.row.generalSUM = "0.00";
            }
            else if (numVal == "annex2C.row.personalLoanNBFCNDSL") {
                annex2C.row.personalLoanNBFCNDSL ="0.00";
                annex2C.row.personalLoanNBFCNDSL1SUM = "0.00";
            }
            else  if (numVal == "annex2C.row.exposureCapMkt") {
                annex2C.row.exposureCapMkt = "0.00";
                annex2C.row.exposureCapMkt1SUM = "0.00";
            }
            else if (numVal == "annex2C.row.standard") {
                annex2C.row.standard = "0.00";
                annex2C.row.standard1SUM = "0.00";
            }
            else if (numVal == "annex2C.row.npaUpgradedStdAsset") {
                annex2C.row.npaUpgradedStdAsset = "0.00";
                annex2C.row.npaUpgradedStdAsset1SUM = "0.00";
            }
            else if (numVal == "annex2C.row.newRestructuredStdACS") {
                annex2C.row.newRestructuredStdACS = "0.00";
                annex2C.row.newRestructuredStdACS1SUM = "0.00";
            }
            else if (numVal == "annex2C.row.memeRestStdAssets") {
                annex2C.row.memeRestStdAssets = "0.00";
                annex2C.row.memeRestStdAssets1SUM = "0.00";
            }
            else if (numVal == "annex2C.row.covid") {
                annex2C.row.covid = "0.00";
                annex2C.row.covid1SUM = "0.00";
            }
            else if (numVal == "annex2C.row.commercialRealEstResdhousing") {
                annex2C.row.commercialRealEstResdhousing = "0.00";
                annex2C.row.commercialRealEstResdhousing1SUM = "0.00";
            }
            else if (numVal == "annex2C.row.expCommRealEst") {
                annex2C.row.expCommRealEst = "0.00";
                annex2C.row.expCommRealEst1SUM = "0.00";
            }
            else if (numVal == "annex2C.row.others") {
                annex2C.row.others = "0.00";
                annex2C.row.others1SUM = "0.00";
            }

            // New Columns Data Here
            else if (numVal == "annex2C.row.wilFul") {
                annex2C.row.wilFul = "0.00";
                annex2C.row.wilFul1SUM = "0.00";
            }else if (numVal == "annex2C.row.secured") {
                annex2C.row.secured = "0.00";
                annex2C.row.secured1SUM = "0.00";
            }else if (numVal == "annex2C.row.unSecured") {
                annex2C.row.unSecured = "0.00";
                annex2C.row.unSecured1SUM = "0.00";
            }else if (numVal == "annex2C.row.restructure") {
                annex2C.row.restructure = "0.00";
                annex2C.row.restructure1SUM = "0.00";
            }else if (numVal == "annex2C.row.nonRestructure") {
                annex2C.row.nonRestructure = "0.00";
                annex2C.row.nonRestructure1SUM = "0.00";
            }
            // New Columns Data Here

            else if (numVal == "annex2C.row.allOthers") {
                annex2C.row.allOthers = "0.00";
                annex2C.row.allOthers1SUM = "0.00";
            }
            else if (numVal == "annex2C.row.total") {
                annex2C.row.total = "0.00";
                annex2C.row.totalSUM = "0.00";
            }

            return false;
        }

        // Not Numeric Value
        if (isNaN(val)) {
            alert("Please enter Numeric Value only");
            if (numVal == "annex2C.row.general") {
                annex2C.row.general = "0.00";
                annex2C.row.generalSUM = "0.00";
            }
            else if (numVal == "annex2C.row.personalLoanNBFCNDSL") {
                annex2C.row.personalLoanNBFCNDSL ="0.00";
                annex2C.row.personalLoanNBFCNDSL1SUM = "0.00";
            }
            else  if (numVal == "annex2C.row.exposureCapMkt") {
                annex2C.row.exposureCapMkt = "0.00";
                annex2C.row.exposureCapMkt1SUM = "0.00";
            }
            else if (numVal == "annex2C.row.standard") {
                annex2C.row.standard = "0.00";
                annex2C.row.standard1SUM = "0.00";
            }
            else if (numVal == "annex2C.row.npaUpgradedStdAsset") {
                annex2C.row.npaUpgradedStdAsset = "0.00";
                annex2C.row.npaUpgradedStdAsset1SUM = "0.00";
            }
            else if (numVal == "annex2C.row.newRestructuredStdACS") {
                annex2C.row.newRestructuredStdACS = "0.00";
                annex2C.row.newRestructuredStdACS1SUM = "0.00";
            }
            else if (numVal == "annex2C.row.memeRestStdAssets") {
                annex2C.row.memeRestStdAssets = "0.00";
                annex2C.row.memeRestStdAssets1SUM = "0.00";
            }
            else if (numVal == "annex2C.row.covid") {
                annex2C.row.covid = "0.00";
                annex2C.row.covid1SUM = "0.00";
            }
            else if (numVal == "annex2C.row.commercialRealEstResdhousing") {
                annex2C.row.commercialRealEstResdhousing = "0.00";
                annex2C.row.commercialRealEstResdhousing1SUM = "0.00";
            }
            else if (numVal == "annex2C.row.expCommRealEst") {
                annex2C.row.expCommRealEst = "0.00";
                annex2C.row.expCommRealEst1SUM = "0.00";
            }
            else if (numVal == "annex2C.row.others") {
                annex2C.row.others = "0.00";
                annex2C.row.others1SUM = "0.00";
            }

            // New Columns Data Here
            else if (numVal == "annex2C.row.wilFul") {
                annex2C.row.wilFul = "0.00";
                annex2C.row.wilFul1SUM = "0.00";
            }else if (numVal == "annex2C.row.secured") {
                annex2C.row.secured = "0.00";
                annex2C.row.secured1SUM = "0.00";
            }else if (numVal == "annex2C.row.unSecured") {
                annex2C.row.unSecured = "0.00";
                annex2C.row.unSecured1SUM = "0.00";
            }else if (numVal == "annex2C.row.restructure") {
                annex2C.row.restructure = "0.00";
                annex2C.row.restructure1SUM = "0.00";
            }else if (numVal == "annex2C.row.nonRestructure") {
                annex2C.row.nonRestructure = "0.00";
                annex2C.row.nonRestructure1SUM = "0.00";
            }
            // New Columns Data Here


            else if (numVal == "annex2C.row.allOthers") {
                annex2C.row.allOthers = "0.00";
                annex2C.row.allOthers1SUM = "0.00";
            }
            else if (numVal == "annex2C.row.total") {
                annex2C.row.total = "0.00";
                annex2C.row.totalSUM = "0.00";
            }
            return false;

        }

        var c = /^(?:\-?\d{1,16}\.\d{1,2}|\-?\d{1,16})$/;
        // var c = /^-?\d{1,16}(\.\d{1,2})?$/;


        if (c.test(val) || val == "") {
            console.log("in if of check c");
            var idot = val.indexOf('.');
            var len = val.lenght;
            console.log("idot 2 zero append:-   "+idot);
            if(idot == -1 ){
                console.log("idot 2 zero append:-");
                if(val == ""){
                    console.log("into blank amount append 0.00");
                    document.getElementById(numId).value = val.concat("0.00");
                }
                else {
                    document.getElementById(numId).value = val.concat(".00");
                    console.log("idot 2 zero append:-   " + idot + "val value:- " + val.concat(".00"))
                }

            }
            else if(idot != -1 && val.charAt(idot+2) == "" ){
                console.log("idot 1 zero append:-");
                document.getElementById(numId).value = val.concat("0");
                console.log("idot 1 zero append:-   "+idot+ "val value:- "+val.concat("0") )
            }
        } else {

            var idotELSE = val.indexOf('.');
            if (idotELSE != -1 && val.split(".")[1].length > 2 ) {
                alert("Maximum 2 decimal digit allowed.");
            } else {
                alert("Amount cannot be greater than 16 digits.");
            }

            if (numVal == "annex2C.row.general") {
                annex2C.row.general = "0.00";
                annex2C.row.generalSUM = "0.00";
            }
            else if (numVal == "annex2C.row.personalLoanNBFCNDSL") {
                annex2C.row.personalLoanNBFCNDSL ="0.00";
                annex2C.row.personalLoanNBFCNDSL1SUM = "0.00";
            }
            else  if (numVal == "annex2C.row.exposureCapMkt") {
                annex2C.row.exposureCapMkt = "0.00";
                annex2C.row.exposureCapMkt1SUM = "0.00";
            }
            else if (numVal == "annex2C.row.standard") {
                annex2C.row.standard = "0.00";
                annex2C.row.standard1SUM = "0.00";
            }
            else if (numVal == "annex2C.row.npaUpgradedStdAsset") {
                annex2C.row.npaUpgradedStdAsset = "0.00";
                annex2C.row.npaUpgradedStdAsset1SUM = "0.00";
            }
            else if (numVal == "annex2C.row.newRestructuredStdACS") {
                annex2C.row.newRestructuredStdACS = "0.00";
                annex2C.row.newRestructuredStdACS1SUM = "0.00";
            }
            else if (numVal == "annex2C.row.memeRestStdAssets") {
                annex2C.row.memeRestStdAssets = "0.00";
                annex2C.row.memeRestStdAssets1SUM = "0.00";
            }
            else if (numVal == "annex2C.row.covid") {
                annex2C.row.covid = "0.00";
                annex2C.row.covid1SUM = "0.00";
            }
            else if (numVal == "annex2C.row.commercialRealEstResdhousing") {
                annex2C.row.commercialRealEstResdhousing = "0.00";
                annex2C.row.commercialRealEstResdhousing1SUM = "0.00";
            }
            else if (numVal == "annex2C.row.expCommRealEst") {
                annex2C.row.expCommRealEst = "0.00";
                annex2C.row.expCommRealEst1SUM = "0.00";
            }
            else if (numVal == "annex2C.row.others") {
                annex2C.row.others = "0.00";
                annex2C.row.others1SUM = "0.00";
            }
            // New Columns Data Here
            else if (numVal == "annex2C.row.wilFul") {
                annex2C.row.wilFul = "0.00";
                annex2C.row.wilFul1SUM = "0.00";
            }else if (numVal == "annex2C.row.secured") {
                annex2C.row.secured = "0.00";
                annex2C.row.secured1SUM = "0.00";
            }else if (numVal == "annex2C.row.unSecured") {
                annex2C.row.unSecured = "0.00";
                annex2C.row.unSecured1SUM = "0.00";
            }else if (numVal == "annex2C.row.restructure") {
                annex2C.row.restructure = "0.00";
                annex2C.row.restructure1SUM = "0.00";
            }else if (numVal == "annex2C.row.nonRestructure") {
                annex2C.row.nonRestructure = "0.00";
                annex2C.row.nonRestructure1SUM = "0.00";
            }
            // New Columns Data Here

            else if (numVal == "annex2C.row.allOthers") {
                annex2C.row.allOthers = "0.00";
                annex2C.row.allOthers1SUM = "0.00";
            }
            else if (numVal == "annex2C.row.total") {
                annex2C.row.total = "0.00";
                annex2C.row.totalSUM = "0.00";
            }
            return false;
        }
        return true;


    }
    // Ended checkNumber Fn.


    // -->>> Redirect to Misc Worklist
    annex2C.gotoMiscWorklist=function ()
    {
        $state.go("circle_maker.miscWorklist");
        $(".modal-backdrop.in").hide();
    }



    // Display Error & Success Message
    annex2C.displayModel=function(data)
    {
        if (data) {
            console.log("Value displayModel Data is: "+data);
            annex2C.displayMessage = "Files Fetched Successfully";

            $('#submitData')
                .modal(
                    {
                        backdrop: 'static',
                        keyboard: false,
                        modal: true
                    });
            $('#submitData')
                .on('shown.bs.modal',
                    function () {
                        $('#submitData')
                            .trigger('focus');
                    });
        }
        else {
            annex2C.displayMessage = "Failed to Fetch Files from CCDP";
            $('#failedSaveSubmit')
                .modal(
                    {
                        backdrop: 'static',
                        keyboard: false,
                        modal: true
                    });
            $('#failedSaveSubmit')
                .on('shown.bs.modal',
                    function () {
                        $('#failedSaveSubmit')
                            .trigger('focus');
                    });
        }
    }


});

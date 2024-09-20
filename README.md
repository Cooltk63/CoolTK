$scope.numberList = ["001", "002", "003", "004", "005"];  // List of 3-digit numbers as strings

// Function to check if a 3-digit number (as a string) exists in the list
$scope.isNumberInList = function(number) {
    return $scope.numberList.includes(number);
};

// Example usage:
var numberToCheck = "003";  // Check for "003"
if ($scope.isNumberInList(numberToCheck)) {
    console.log(numberToCheck + " exists in the list.");
} else {
    console.log(numberToCheck + " does not exist in the list.");
}
public List<List<String>> processResult(List<List<String>> result) {
    for (List<String> row : result) {
        for (int i = 0; i < row.size(); i++) {
            if ("NULL".equals(row.get(i))) {
                row.set(i, "");  // Replace "NULL" with an empty string
            }
        }
    }
    return result;
}
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;
import java.util.List;

@Service
public class MyDataService {

    @Autowired
    private MyDataRepository myDataRepository;

    public void saveData(List<List<String>> dataList) {
        for (List<String> data : dataList) {
            // Assumes each list has exactly 8 elements
            MyDataEntity entity = new MyDataEntity(
                data.get(0), data.get(1), data.get(2), data.get(3),
                data.get(4), data.get(5), data.get(6), data.get(7)
            );
            myDataRepository.save(entity);
        }
    }
}
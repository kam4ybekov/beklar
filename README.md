# beklar 
import java.util.HashMap;
import java.util.Map;

public class RacingApp {

    public static void main(String[] args) {
        Map<String, Integer> racers = new HashMap<>();
        racers.put("мотциклист1", 200);
        racers.put("мотциклист2", 180);
        racers.put("мотциклист3", 210);
        racers.put("мотциклист4", 190);

        double averageSpeed = racers.values().stream()
                .mapToInt(Integer::intValue)
                .average()
                .orElse(0);


        Map<String, Integer> fastRacers = new HashMap<>();

        for (Map.Entry<String, Integer> entry : racers.entrySet()) {
            String name = entry.getKey();
            int speed = entry.getValue();
            if (speed >= averageSpeed) {
                fastRacers.put(name, speed);
            }
        }

        System.out.println("Средняя скорость: " + averageSpeed);
        System.out.println("Гонщики с скоростью выше или равной средней: " + fastRacers);
    }
}

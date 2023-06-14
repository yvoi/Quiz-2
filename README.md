#temp
import java.util.Scanner;

public class TemperatureMonitoringSystem {

    private int[][] temperatures;

    public static void main(String[] args) {

        TemperatureMonitoringSystem monitoringSystem = new TemperatureMonitoringSystem();

        monitoringSystem.run();

    }

    public void run() {

        int daysPerWeek = getDaysPerWeek();

        temperatures = new int[daysPerWeek][];

        collectTemperatures(daysPerWeek);

        printAllTemperatures();

        printMaxAndMinTemperature();

        printNegativeTemperatures();

        printAverageTemperature();

    }

    public int getDaysPerWeek() {

        Scanner scanner = new Scanner(System.in);

        System.out.print("Informe o número de dias por semana a serem mapeados: ");

        return scanner.nextInt();

    }

    public void collectTemperatures(int daysPerWeek) {

        Scanner scanner = new Scanner(System.in);

        for (int i = 0; i < daysPerWeek; i++) {

            System.out.print("Informe as temperaturas médias para o dia " + (i + 1) + ": ");

            int numTemperatures = scanner.nextInt();

            temperatures[i] = new int[numTemperatures];

            for (int j = 0; j < numTemperatures; j++) {

                temperatures[i][j] = scanner.nextInt();

            }

        }

    }

    public void printAllTemperatures() {

        System.out.println("Temperaturas mapeadas:");

        for (int i = 0; i < temperatures.length; i++) {

            System.out.print("Dia " + (i + 1) + ": ");

            for (int j = 0; j < temperatures[i].length; j++) {

                System.out.print(temperatures[i][j] + " ");

            }

            System.out.println();

        }

    }

    public void printMaxAndMinTemperature() {

        int maxTemperature = Integer.MIN_VALUE;

        int minTemperature = Integer.MAX_VALUE;

        for (int[] temperatureArray : temperatures) {

            for (int temperature : temperatureArray) {

                maxTemperature = Math.max(maxTemperature, temperature);

                minTemperature = Math.min(minTemperature, temperature);

            }

        }

        System.out.println("Maior temperatura: " + maxTemperature);

        System.out.println("Menor temperatura: " + minTemperature);

    }

    public void printNegativeTemperatures() {

        System.out.println("Temperaturas negativas:");

        for (int[] temperatureArray : temperatures) {

            for (int temperature : temperatureArray) {

                if (temperature < 0) {

                    System.out.println(temperature);

                }

            }

        }

    }

    public void printAverageTemperature() {

        int totalTemperatures = 0;


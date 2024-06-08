# wordcount
package wordcountproject1;
import java.io.BufferedReader;
import java.io.FileReader;
import java.io.IOException;
import java.util.HashMap;
import java.util.Map;
import java.util.TreeMap;

public class  Wordcountproject1 {
    public static void main(String[] args) {
        // Path to the text file
        String filePath = ("C:/Users/Anasua Mazumdar/Desktop/wordcount"); // Replace with the actual file path
        
        // HashMap to store the word counts
        HashMap<String, Integer> wordCounts = new HashMap<>();
        
        // Read the file and count the word occurrences
        try (BufferedReader br = new BufferedReader(new FileReader(filePath))) {
            String line;
            while ((line = br.readLine()) != null) {
                // Split the line into words
                String[] words = line.toLowerCase().replaceAll("[^a-zA-Z\\s]", "").split("\\s+");
                for (String word : words) {
                    if (word.length() > 0) {
                        wordCounts.put(word, wordCounts.getOrDefault(word, 0) + 1);
                    }
                }
            }
        } catch (IOException e) {
        }
        
        // Use TreeMap to sort the words alphabetically
        TreeMap<String, Integer> sortedWordCounts = new TreeMap<>(wordCounts);
        
        // Display the word counts
        for (Map.Entry<String, Integer> entry : sortedWordCounts.entrySet())
        {
            System.out.println(entry.getKey() + ": " + entry.getValue());
        }
    }
}



# FindMissingFilename

Problem: You have a Database that stores unix timestamps as keys, and a list of filenames that were saved at that timestamp.

DB Key(Timestamps) Values 2. \["filename1", "filename2"] 4. \["filename3"] 10. \["filename6", "filename7"]

5 elements

We copied the database to a different region and we lost one value:

DB\_COPY Key. Values 2. \["filename1"] 4. \["filename3"] 10. \["filename6", "filename7"]

4 elements

We need to create a function that returns the missing string.

We do not need to implement this functions, but they can help you. int CountFilenames(int start\_time, int end\_time); // Counts filenames in timerange, inclusive of endpoints.

List GetFilenames(int timestamp); // Gets all filenames at a timestamp

FindMissingFilename(DB, DB\_COPY, 2, 10) -> "filename2" \*/in java



```
import java.util.List;

public class Main {
    public static String FindMissingFilename(DB originalDB, DB copyDB, int start_time, int end_time) {
        for (int timestamp = start_time; timestamp <= end_time; timestamp++) {
            List<String> originalFilenames = originalDB.GetFilenames(timestamp);
            List<String> copyFilenames = copyDB.GetFilenames(timestamp);

            if (originalFilenames.size() != copyFilenames.size()) {
                // The number of filenames at this timestamp is different, there is a missing filename
                for (String filename : originalFilenames) {
                    if (!copyFilenames.contains(filename)) {
                        return filename;
                    }
                }
            }
        }

        return null;  // No missing filename found
    }
}
```

```
import java.util.HashSet;
import java.util.List;
import java.util.Set;

public class Main {
    public static String FindMissingFilename(DB originalDB, DB copyDB, int start_time, int end_time) {
        Set<String> originalFilenames = new HashSet<>();
        Set<String> copyFilenames = new HashSet<>();

        // Collect all filenames in the original DB within the given time range
        for (int timestamp = start_time; timestamp <= end_time; timestamp++) {
            originalFilenames.addAll(originalDB.GetFilenames(timestamp));
        }

        // Collect all filenames in the copy DB within the given time range
        for (int timestamp = start_time; timestamp <= end_time; timestamp++) {
            copyFilenames.addAll(copyDB.GetFilenames(timestamp));
        }

        // Find the missing filename
        for (String filename : originalFilenames) {
            if (!copyFilenames.contains(filename)) {
                return filename;
            }
        }

        return null;  // No missing filename found
    }
}
```

```
import java.util.List;

public class Main {
    public static String FindMissingFilename(DB originalDB, DB copyDB, int start_time, int end_time) {
        for (int timestamp = start_time; timestamp <= end_time; timestamp++) {
            List<String> originalFilenames = originalDB.GetFilenames(timestamp);
            List<String> copyFilenames = copyDB.GetFilenames(timestamp);

            if (originalFilenames.size() != copyFilenames.size()) {
                // The number of filenames at this timestamp is different, there is a missing filename

                int left = 0;
                int right = originalFilenames.size() - 1;

                while (left <= right) {
                    int mid = left + (right - left) / 2;
                    String originalFilename = originalFilenames.get(mid);
                    String copyFilename = copyFilenames.get(mid);

                    if (!originalFilename.equals(copyFilename)) {
                        // Filenames at this position are different, the missing filename is in the left half
                        right = mid - 1;
                    } else {
                        // Filenames at this position are the same, search in the right half
                        left = mid + 1;
                    }
                }

                return originalFilenames.get(left);
            }
        }

        return null;  // No missing filename found
    }
}

```

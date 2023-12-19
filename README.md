# madhu-cloud-vandana-answers
# 1. JAVA
# A. Create an array with the values (1, 2, 3, 4, 5, 6, 7) and shuffle it.
import java.util.Arrays;
import java.util.Collections;
import java.util.List;

public class ShuffleArray {
    public static void main(String[] args) {
        Integer[] array = {1, 2, 3, 4, 5, 6, 7};

        // Convert array to list for shuffling
        List<Integer> list = Arrays.asList(array);
        Collections.shuffle(list);

        // Convert list back to array
        Integer[] shuffledArray = list.toArray(new Integer[0]);

        // Print shuffled array
        System.out.println(Arrays.toString(shuffledArray));
    }
}
# B. Enter a Roman Number as input and convert it to an integer. (ex IX = 9)
import java.util.HashMap;
import java.util.Map;

public class RomanToInteger {
    public static void main(String[] args) {
        String romanNumber = "IX";
        int result = romanToInt(romanNumber);
        System.out.println("The integer value of " + romanNumber + " is: " + result);
    }

    public static int romanToInt(String s) {
        Map<Character, Integer> romanMap = new HashMap<>();
        romanMap.put('I', 1);
        romanMap.put('V', 5);
        romanMap.put('X', 10);
        romanMap.put('L', 50);
        romanMap.put('C', 100);
        romanMap.put('D', 500);
        romanMap.put('M', 1000);

        int result = 0;

        for (int i = 0; i < s.length(); i++) {
            int current = romanMap.get(s.charAt(i));
            int next = (i + 1 < s.length()) ? romanMap.get(s.charAt(i + 1)) : 0;

            if (current < next) {
                result += (next - current);
                i++;  // Skip the next character
            } else {
                result += current;
            }
        }

        return result;
    }
}
# C. Check if the input is pangram or not. (Pangram is a sentence that contains all the alphabet
# from a-z)
public class PangramChecker {
    public static void main(String[] args) {
        String input = "The quick brown fox jumps over the lazy dog";
        boolean isPangram = isPangram(input.toLowerCase());
        System.out.println("Is it a pangram? " + isPangram);
    }

    public static boolean isPangram(String s) {
        boolean[] alphabetPresent = new boolean[26];

        for (char c : s.toCharArray()) {
            if (Character.isLetter(c)) {
                alphabetPresent[c - 'a'] = true;
            }
        }

        // Check if all letters are present
        for (boolean present : alphabetPresent) {
            if (!present) {
                return false;
            }
        }

        return true;
    }
}
# 2 JavaScript
# A. Take a sentence as an input and reverse every word in that sentence.
function reverseWords(sentence) {
    let words = sentence.split(' ');
    let reversedWords = words.map(word => reverseWord(word));
    let reversedSentence = reversedWords.join(' ');
    return reversedSentence;
}
function reverseWord(word) {
    return word.split('').reverse().join('');
}
let inputSentence = "This is a sunny day";
let reversedResult = reverseWords(inputSentence);
console.log(reversedResult);

# B. Perform sorting of an array in descending order.
function sortArrayDescending(arr) {
    return arr.sort((a, b) => b - a);
}
# example usage
let inputArray = [5, 2, 9, 1, 5, 6];
let sortedArray = sortArrayDescending(inputArray);
console.log(sortedArray);

# 3. HTML
# A. Create a basic calculator using HTML, CSS, and JavaScript with the functionality of add,
# subtract, multiply and divide. Use the following picture for reference.
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="style.css">
    <title>Basic Calculator</title>
</head>
<body>
    <div class="calculator">
        <input type="text" id="display" disabled>
        <div class="buttons">
            <button onclick="clearDisplay()">C</button>
            <button onclick="appendToDisplay('/')">/</button>
            <button onclick="appendToDisplay('*')">*</button>
            <button onclick="appendToDisplay('7')">7</button>
            <button onclick="appendToDisplay('8')">8</button>
            <button onclick="appendToDisplay('9')">9</button>
            <button onclick="appendToDisplay('-')">-</button>
            <button onclick="appendToDisplay('4')">4</button>
            <button onclick="appendToDisplay('5')">5</button>
            <button onclick="appendToDisplay('6')">6</button>
            <button onclick="appendToDisplay('+')">+</button>
            <button onclick="appendToDisplay('1')">1</button>
            <button onclick="appendToDisplay('2')">2</button>
            <button onclick="appendToDisplay('3')">3</button>
            <button onclick="calculateResult()">=</button>
            <button onclick="appendToDisplay('0')">0</button>
            <button onclick="appendToDisplay('.')">.</button>
        </div>
    </div>
    <script src="script.js"></script>
</body>
</html>

# B. Create a survey form with Fields; First Name, Last Name, Date of Birth, Country (dropdown),
# Gender (checkbox), Profession, email, and mobile number. All the input fields are
# necessary to submit the form. Create two buttons Submit and Reset. Reset will reset the
# form while clicking on submit, first, it will check all the fields and necessary validations and
# then a popup will appear displaying all the selected values with the label in front of it. On
# closing the popup, the form should reset all the values. Use the following for reference

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Survey Form</title>
    <style>
        body {
            font-family: Arial, sans-serif;
        }
        form {
            max-width: 400px;
            margin: 0 auto;
        }
        .popup {
            display: none;
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            padding: 20px;
            background-color: #f1f1f1;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }
    </style>
</head>
<body>

<form id="surveyForm">
    <label for="firstName">First Name:</label>
    <input type="text" id="firstName" name="firstName" required>

    <label for="lastName">Last Name:</label>
    <input type="text" id="lastName" name="lastName" required>

    <label for="dob">Date of Birth:</label>
    <input type="date" id="dob" name="dob" required>

    <label for="country">Country:</label>
    <select id="country" name="country" required>
        <option value="us">United States</option>
        <option value="ca">Canada</option>
        <!-- Add more countries as needed -->
    </select>

    <label>Gender:</label>
    <input type="checkbox" id="male" name="gender" value="male"> <label for="male">Male</label>
    <input type="checkbox" id="female" name="gender" value="female"> <label for="female">Female</label>

    <label for="profession">Profession:</label>
    <input type="text" id="profession" name="profession" required>

    <label for="email">Email:</label>
    <input type="email" id="email" name="email" required>

    <label for="mobile">Mobile Number:</label>
    <input type="tel" id="mobile" name="mobile" required>

    <button type="button" onclick="submitForm()">Submit</button>
    <button type="button" onclick="resetForm()">Reset</button>
</form>

<div id="popup" class="popup"></div>

<script>
    function submitForm() {
        // Validate and submit form
        // Sample validation: Check if all required fields are filled
        var form = document.getElementById('surveyForm');
        if (form.checkValidity()) {
            // Get form values
            var firstName = document.getElementById('firstName').value;
            var lastName = document.getElementById('lastName').value;
            var dob = document.getElementById('dob').value;
            var country = document.getElementById('country').value;
            var gender = [...document.getElementsByName('gender')].filter(checkbox => checkbox.checked).map(checkbox => checkbox.value);
            var profession = document.getElementById('profession').value;
            var email = document.getElementById('email').value;
            var mobile = document.getElementById('mobile').value;

            // Display values in popup
            var popupContent = `
                <p><strong>First Name:</strong> ${firstName}</p>
                <p><strong>Last Name:</strong> ${lastName}</p>
                <p><strong>Date of Birth:</strong> ${dob}</p>
                <p><strong>Country:</strong> ${country}</p>
                <p><strong>Gender:</strong> ${gender.join(', ')}</p>
                <p><strong>Profession:</strong> ${profession}</p>
                <p><strong>Email:</strong> ${email}</p>
                <p><strong>Mobile Number:</strong> ${mobile}</p>
            `;

            document.getElementById('popup').innerHTML = popupContent;
            document.getElementById('popup').style.display = 'block';

            // Reset form
            form.reset();
        } else {
            alert('Please fill out all required fields.');
        }
    }

    function resetForm() {
        // Reset form
        document.getElementById('surveyForm').reset();
    }

    function closePopup() {
        // Close popup
        document.getElementById('popup').style.display = 'none';
    }
</script>

</body>
</html>




# Solution_ASE
# 1.Java
# A.Create an array with the values (1, 2, 3, 4, 5, 6, 7) and shuffle it.
# Code
import java.util.Arrays;
import java.util.Random;

class solution
{
	public static void shuffle(int nums[])
	{
		for (int i = nums.length - 1; i >= 1; i--)
		{
			Random rand = new Random();

			int j = rand.nextInt(i + 1);

			swap_elements(nums, i, j);
		}
	}
        private static void swap_elements(int[] nums, int i, int j) {
		int temp = nums[i];
		nums[i] = nums[j];
		nums[j] = temp;
	}
	public static void main (String[] args)
	{
		int[] nums = { 1, 2, 3, 4, 5, 6 };
        System.out.println(Arrays.toString(nums));
		shuffle(nums);
		System.out.println(Arrays.toString(nums));
	}
}

# B. Enter a Roman Number as input and convert it to an integer.
# Code 
import java.util.HashMap;
import java.util.Map;
import java.util.Scanner;

public class RomanToInteger {
    public static int romanToInt(String s) {
        Map<Character, Integer> romanValues = new HashMap<>();
        romanValues.put('I', 1);
        romanValues.put('V', 5);
        romanValues.put('X', 10);
        romanValues.put('L', 50);
        romanValues.put('C', 100);
        romanValues.put('D', 500);
        romanValues.put('M', 1000);

        int result = 0;
        int prevValue = 0;

        for (int i = s.length() - 1; i >= 0; i--) {
            int value = romanValues.get(s.charAt(i));
            if (value < prevValue) {
                result -= value;
            } else {
                result += value;
            }
            prevValue = value;
        }

        return result;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print(" ");
        String romanNumeral = scanner.nextLine().toUpperCase();
        int integerEquivalent = romanToInt(romanNumeral);

        System.out.println(integerEquivalent);
    }
}

# C.Check if the input is pangram or not.
# Code
import java.util.HashSet;
import java.util.Scanner;

public class PangramChecker {
    public static boolean isPangram(String input) {
        input = input.toLowerCase().replaceAll(" ", "");
        HashSet<Character> letters = new HashSet<>();

        for (int i = 0; i < input.length(); i++) {
            char c = input.charAt(i);
            if (Character.isLetter(c)) {
                letters.add(c);
            }
        }

        return letters.size() == 26;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter a sentence: ");
        String input = scanner.nextLine();
        scanner.close();

        boolean isPangram = isPangram(input);

        if (isPangram) {
            System.out.println("The input is a pangram.");
        } else {
            System.out.println("The input is not a pangram.");
        }
    }
}

# 2.JavaScript
# A.Take a sentence as an input and reverse every word in that sentence. 
# Code
function reverseWords(sentence) {
    let words = sentence.split(' ');
    let reversedWords = words.map(word => {
        return word.split('').reverse().join('');
    });
    return reversedWords.join(' ');
}

const readline = require('readline');
const rl = readline.createInterface({
    input: process.stdin,
    output: process.stdout
});

rl.question("Enter a sentence: ", function(sentence) {
    const reversedSentence = reverseWords(sentence);
    console.log("Reversed sentence: " + reversedSentence);
    rl.close();
});

# B.Perform sorting of an array in descending order. 
# Code
function sortArrayDescending(arr) {
    arr.sort(function(a, b) {
        return b - a; // Compare elements in descending order
    });
}

const numbers = [5, 2, 9, 1, 5, 6];
sortArrayDescending(numbers);
console.log(numbers);

# 3.HTML
# A. Create a basic calculator using HTML, CSS, and JavaScript with the functionality of add,subtract, multiply and divide.
# 1-HTML Code
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" type="text/css" href="style.css">
    <title>Basic Calculator</title>
</head>
<body>
    <div class="calculator">
        <input type="text" id="display" readonly>
        <div class="buttons">
            <button class="operator" onclick="appendToDisplay('7')">7</button>
            <button class="operator" onclick="appendToDisplay('8')">8</button>
            <button class="operator" onclick="appendToDisplay('9')">9</button>
            <button class="operator" onclick="appendToDisplay('+')">+</button>
            <button class="operator" onclick="appendToDisplay('4')">4</button>
            <button class="operator" onclick="appendToDisplay('5')">5</button>
            <button class="operator" onclick="appendToDisplay('6')">6</button>
            <button class="operator" onclick="appendToDisplay('-')">-</button>
            <button class="operator" onclick="appendToDisplay('1')">1</button>
            <button class="operator" onclick="appendToDisplay('2')">2</button>
            <button class="operator" onclick="appendToDisplay('3')">3</button>
            <button class="operator" onclick="appendToDisplay('*')">*</button>
            <button class="operator" onclick="appendToDisplay('0')">0</button>
            <button class="operator" onclick="appendToDisplay('.')">.</button>
            <button class="operator" onclick="appendToDisplay('/')">/</button>
            <button class="equals" onclick="calculate()">=</button>
            <button class="clear" onclick="clearDisplay()">C</button>
        </div>
    </div>
    <script src="script.js"></script>
</body>
</html>

# 2-CSS Code
body {
    font-family: Arial, sans-serif;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    margin: 0;
    background-color: #f0f0f0;
}

.calculator {
    width: 300px;
    padding: 20px;
    border: 2px solid #333;
    border-radius: 10px;
    text-align: center;
    background-color: #333;
    color: #fff;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
}

#display {
    width: 100%;
    margin-bottom: 10px;
    padding: 5px;
    font-size: 24px;
    border: none;
    border-radius: 5px;
    text-align: right;
    background-color: #444;
    color: #fff;
}

.buttons {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-gap: 5px;
}

button {
    width: 100%;
    height: 60px;
    font-size: 20px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
}

.operator {
    background-color: #555;
    color: #fff;
}

.operator:hover {
    background-color: #777;
}

.equals {
    background-color: #3F51B5;
    color: #fff;
}

.equals:hover {
    background-color: #303F9F;
}

.clear {
    background-color: #F44336;
    color: #fff;
}

.clear:hover {
    background-color: #D32F2F;
}

# 3-JavaScript Code
let currentInput = '';

function appendToDisplay(value) {
    currentInput += value;
    document.getElementById('display').value = currentInput;
}

function clearDisplay() {
    currentInput = '';
    document.getElementById('display').value = '';
}

function calculate() {
    try {
        currentInput = eval(currentInput).toString();
        document.getElementById('display').value = currentInput;
    } catch (error) {
        currentInput = '';
        document.getElementById('display').value = 'Error';
    }
}

# B. Create a survey form with Fields; First Name, Last Name, Date of Birth, Country (dropdown),Gender (checkbox), Profession, email, and mobile number. All the input fields are necessary to submit the form. Create two buttons Submit and Reset. Reset will reset the form while clicking on submit, first, it will check all the fields and necessary validations and then a popup will appear displaying all the selected values with the label in front of it. On closing the popup, the form should reset all the values.
# 1-HTML Code
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" type="text/css" href="style.css">
    <title>Survey Form</title>
</head>
<body>
    <div class="container">
        <h1>Survey Form</h1>
        <form id="surveyForm">
            <label for="firstName">First Name:</label>
            <input type="text" id="firstName" required><br><br>

            <label for="lastName">Last Name:</label>
            <input type="text" id="lastName" required><br><br>

            <label for="dob">Date of Birth:</label>
            <input type="date" id="dob" required><br><br>

            <label for="country">Country:</label>
            <select id="country" required>
                <option value="">Select Country</option>
                <option value="India">India</option>
                <option value="USA">USA</option>
                <option value="Canada">Canada</option>
                <option value="UK">UK</option>
                <option value="France">France</option>
                
            </select><br><br>

            <label>Gender:</label>
            <input type="checkbox" id="male" name="gender" value="Male">
            <label for="male">Male</label>
            <input type="checkbox" id="female" name="gender" value="Female">
            <label for="female">Female</label>
            <input type="checkbox" id="other" name="gender" value="Other">
            <label for="other">Other</label><br><br>

            <label for="profession">Profession:</label>
            <input type="text" id="profession" required><br><br>

            <label for="email">Email:</label>
            <input type="email" id="email" required><br><br>

            <label for="mobile">Mobile Number:</label>
            <input type="tel" id="mobile" required><br><br>

            <button type="button" id="submitBtn">Submit</button>
            <button type="reset" id="resetBtn">Reset</button>
        </form>

        <div class="popup" id="popup">
            <span class="close" id="closePopupBtn">&times;</span>
            <h2>Survey Form Submission</h2>
            <div id="popupContent"></div>
        </div>
    </div>

    <script src="script.js"></script>
</body>
</html>

# 2-CSS Code
body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
    background-color: #f0f0f0;
}

.container {
    background-color: #fff;
    max-width: 500px;
    margin: 0 auto;
    padding: 20px;
    border: 2px solid #333;
    border-radius: 10px;
    text-align: center;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
}

form {
    text-align: left;
}

label {
    font-weight: bold;
}

input[type="text"],
input[type="date"],
select,
input[type="email"],
input[type="tel"] {
    width: 100%;
    padding: 5px;
    font-size: 16px;
    border: 1px solid #ccc;
    border-radius: 5px;
    margin-top: 5px;
}

button[type="button"],
button[type="reset"] {
    width: 49%;
    height: 40px;
    font-size: 16px;
    margin-top: 10px;
}

.popup {
    display: none;
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    background-color: #fff;
    max-width: 80%;
    border: 2px solid #333;
    border-radius: 10px;
    text-align: center;
    padding: 20px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
}

.close {
    position: absolute;
    top: 10px;
    right: 10px;
    cursor: pointer;
    font-size: 24px;
    font-weight: bold;
}

# 3-JavaScript Code
document.addEventListener("DOMContentLoaded", function() {
    const surveyForm = document.getElementById("surveyForm");
    const popup = document.getElementById("popup");
    const popupContent = document.getElementById("popupContent");
    const closePopupBtn = document.getElementById("closePopupBtn");

    surveyForm.addEventListener("submit", function(event) {
        event.preventDefault();
        showPopup();
    });

    closePopupBtn.addEventListener("click", function() {
        hidePopup();
    });
});

function showPopup() {
    const firstName = document.getElementById("firstName").value;
    const lastName = document.getElementById("lastName").value;
    const dob = document.getElementById("dob").value;
    const country = document.getElementById("country").value;
    const genderCheckboxes = document.querySelectorAll('input[name="gender"]:checked');
    const gender = Array.from(genderCheckboxes).map(checkbox => checkbox.value).join(', ');
    const profession = document.getElementById("profession").value;
    const email = document.getElementById("email").value;
    const mobile = document.getElementById("mobile").value;

    const results = `
        <p><strong>First Name:</strong> ${firstName}</p>
        <p><strong>Last Name:</strong> ${lastName}</p>
        <p><strong>Date of Birth:</strong> ${dob}</p>
        <p><strong>Country:</strong> ${country}</p>
        <p><strong>Gender:</strong> ${gender}</p>
        <p><strong>Profession</p>

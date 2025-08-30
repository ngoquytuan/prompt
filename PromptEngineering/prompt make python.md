Here's a detailed prompt designed to get you a well-commented, easy-to-maintain Python program on Windows. It covers various aspects to ensure the AI understands your needs thoroughly:

---

**Prompt:**

"I need a Python program for Windows. The code should be fully commented, with an emphasis on clarity and easy maintainability. Please consider the following aspects when generating the code:

**1. Project Goal/Problem to Solve (Choose ONE or specify your own):**

- **Option A: Simple File Organizer:** Create a script that can organize files in a specified directory based on their extension (e.g., move all `.jpg` files to a 'Pictures' folder, all `.txt` files to a 'Documents' folder).
- **Option B: Basic Data Logger:** Develop a program that logs simple data (e.g., timestamp, user input string) to a text file, with options to append or overwrite.
- **Option C: Desktop Notifier:** Build a script that displays a desktop notification (using a library like `plyer` or a similar Windows-specific method) with a custom message and title after a certain interval or upon an event.
- **Option D: Simple Calculator GUI (Tkinter):** Create a basic calculator with a graphical user interface using `tkinter` that performs addition, subtraction, multiplication, and division.
- **Option E: Custom:** \[**Describe your specific project goal here in detail.** The more specific you are, the better the output will be.\]

**2. Key Features/Functionality (tailor to your chosen project):**

- **For File Organizer:**
  - Specify source directory.
  - Specify destination directories for different file types.
  - Handle existing destination folders (create if not present).
  - Provide feedback on moved files.
- **For Data Logger:**
  - Allow user to choose between appending to an existing log file or creating a new one.
  - Include a timestamp for each log entry.
  - Error handling for file operations.
- **For Desktop Notifier:**
  - Set notification title and message.
  - Define notification duration.
  - Ability to trigger manually or based on a simple timer.
- **For Simple Calculator GUI:**
  - Basic arithmetic operations (+, -, \*, /).
  - Clear button.
  - Display results.
  - Error handling for division by zero or invalid input.
- **For Custom Project:** \[**List specific features here.**\]

**3. Code Structure and Maintainability Requirements:**

- **Modular Design:** Break down the code into functions and, if appropriate for the complexity, classes.
- **Clear Variable Names:** Use descriptive variable names (e.g., `source_directory` instead of `src`).
- **Constants:** Define constants for unchanging values (e.g., file paths, magic numbers) at the top of the script or in a dedicated section.
- **Error Handling:** Implement robust `try-except` blocks for file operations, user input, and other potential failure points.
- **Input Validation:** Validate user inputs to prevent unexpected behavior.
- **Docstrings:** Include clear docstrings for all functions and classes, explaining their purpose, arguments, and return values.
- **Inline Comments:** Use concise inline comments to explain complex logic or non-obvious steps.
- **Readability:** Adhere to PEP 8 guidelines for code formatting (indentation, whitespace, etc.).
- **No Hardcoded Paths (if applicable):** Where possible, use relative paths or prompt the user for directory selection. If absolute paths are necessary for demonstration, make them easily modifiable.
- **Dependencies:** List any external libraries required and provide instructions for installation (e.g., `pip install library_name`).

**4. Windows-Specific Considerations:**

- **Path Handling:** Use `os.path.join` for constructing paths to ensure cross-platform compatibility (even though it's for Windows, it's good practice).
- **Desktop Notifications:** If applicable, suggest or use a suitable library for Windows desktop notifications (e.g., `plyer`, `win10toast` if compatible with your environment, or direct Windows API calls if the AI can manage that simply).
- **User Interface (if applicable):** If a GUI is requested, `tkinter` is the preferred built-in library for simplicity on Windows.

**5. Example Usage/Instructions:**

- Provide a brief "How to Run" section, explaining any setup steps (like installing libraries) and how to execute the script.
- Include example inputs if the program requires user interaction.

---

**Example of a good specific request (if you choose Option A):**

"I need a Python program for Windows that organizes files in a specified directory. The program should move `.jpg`, `.png`, and `.gif` files to a 'Images' folder, `.txt` and `.pdf` files to a 'Documents' folder, and `.mp3` and `.wav` files to an 'Audio' folder within the same parent directory as the source.

The code should be fully commented, with an emphasis on clarity and easy maintainability. It must have a modular design with functions for file moving, directory creation, and user input. Variable names should be descriptive, and constants should be used for folder names and file extensions. Robust error handling for file operations and directory creation is essential. Include clear docstrings for all functions and concise inline comments for complex logic. Use `os.path.join` for path handling. Provide clear instructions on how to run the script, including any necessary library installations. If a destination folder doesn't exist, the program should create it."

---
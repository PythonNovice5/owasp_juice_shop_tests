# OWASP Juice Shop Test Suite

## Description
This project is a test suite for the OWASP Juice Shop, designed to ensure that key functionalities of the application work as expected. The test suite includes cases for verifying pagination, items per page, language changes, login functionality, and more.

## Building and Running the Application with Docker

Using Docker is a straightforward way to set up and run the OWASP Juice Shop application. Follow these steps to get it running:

### Prerequisites
- **Docker**: Ensure Docker is installed on your machine. You can download it from [docker.com](https://www.docker.com/products/docker-desktop).

### Instructions

1. **Install Docker**: Follow the installation instructions for your operating system from the [Docker website](https://docs.docker.com/get-docker/).

2. **Pull the Juice Shop Docker Image**:
   ```bash
   docker pull bkimminich/juice-shop
   ```

3. **Run the Juice Shop Docker Container**:
   ```bash
   docker run --rm -p 3000:3000 bkimminich/juice-shop
   ```

   This command runs the Juice Shop container and maps port 3000 on your host machine to port 3000 in the container.

4. **Access the Application**:
   - Open your web browser and navigate to [http://localhost:3000](http://localhost:3000) if you are using Docker natively.
   - If you are using Docker Machine on macOS or Windows, browse to [http://192.168.99.100:3000](http://192.168.99.100:3000).

## Installation of Test Suite

### Prerequisites
- **Python**: Ensure Python is installed. You can download it from [python.org](https://www.python.org/).
- **Git**: Required for cloning the test suite repository.
- **pytest**: The test suite uses `pytest` for running tests. You can install it using `pip`.

### Instructions

1. **Clone the Test Suite Repository**:
   ```bash
   git clone https://github.com/PythonNovice5/owasp_juice_shop_tests.git
   ```

2. **Navigate to the Test Suite Directory**:
   ```bash
   cd owasp_juice_shop_tests
   ```

3. **Create and Activate a Virtual Environment** (optional but recommended):
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
   ```

4. **Install Dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

   Ensure you have a `requirements.txt` file in your repository that lists `pytest` and any other dependencies.

5. **Configure the Test Environment**:
   Update the configuration file with the URL of the running Juice Shop instance. This is usually done in a configuration file or an environment variable.

## Usage

## Running Tests
   **1. Running all tests via pytest command on Windows/Linux** 
  
  ```
  Go to project directory owasp_juice_shop_tests (cd owasp_juice_shop_tests)
  python -m pytest -v -s --headless --html=report.html tests
  ```
   **2. Running smoke(functional) tests via pytest command on Windows/Linux** 
  
  ```
  Go to project directory owasp_juice_shop_tests (cd owasp_juice_shop_tests)
  python -m pytest -v -s --headless --html=report.html -m smoke
  ```

  **3. Running  security tests via pytest command on Windows/Linux as HeadLess browser**
  
  ```
  Go to project directory lynx_tests_assignment (cd lynx_tests_assignment)
  python -m pytest -v -s --headless --html=report.html -m security
  ``` 
  **4. Running tests via pytest command on Windows/Linux browser head**
  
  ```
  Remove the argument --headless in the commands in steps 1-3 above, run the remaining
  ``` 

This command will execute all the test cases defined in the test suite.

## Test Cases

Below are the test cases included in this test suite:

### 1. Pagination Functionality
- **Objective**: Ensure pagination functionality displays different items per page.
- **Test Steps**:
  1. Navigate to the product listing page.
  2. Verify that pagination is present and functional.
  3. Check that different items are displayed when navigating through pages.

### 2. Items Per Page
- **Objective**: Verify that changing the amount of items per page lists the correct number of items.
- **Test Steps**:
  1. Navigate to the product listing page.
  2. Change the number of items displayed per page using the pagination controls.
  3. Verify that the correct number of items is shown according to the selection.

### 3. Language Change
- **Objective**: Ensure that changing the language adjusts the header and sidebar menu labels.
- **Test Steps**:
  1. Change the application language.
  2. Verify that the header label ‘All products’ and sidebar menu labels are updated to the selected language.

### 4. Invalid Login Credentials
- **Objective**: Verify that the login form returns an error message for invalid user/password combinations.
- **Test Steps**:
  1. Attempt to log in with invalid credentials.
  2. Verify that an appropriate error message is displayed.

### 5. Valid Login Credentials
- **Objective**: Ensure that using valid credentials successfully logs in and shows the correct response messages.
- **Test Steps**:
  1. Log in with the following credentials:
     - **Username**: `admin@juice-sh.op`
     - **Password**: `admin123`
  2. Verify that the login is successful and the expected response messages are displayed.

## Contributing

If you'd like to contribute to this test suite, please fork the repository, create a branch, and submit a pull request. For detailed guidelines, see the [CONTRIBUTING.md](CONTRIBUTING.md) file.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contact

For any questions or feedback, you can reach out to:

- [Your Name](https://github.com/your-username)
- Email: you@example.com
- Project Link: [https://github.com/username/repository-name](https://github.com/username/repository-name)
```

### Key Changes:
- **Python and pytest**: Updated the instructions to use Python and `pytest` instead of Node.js and `npm`.
- **Virtual Environment**: Added instructions for creating and activating a Python virtual environment.
- **Dependencies**: Assumed the presence of a `requirements.txt` file for dependencies.

Replace placeholders with your actual repository URL, personal information, and any specific configuration details relevant to your test environment.

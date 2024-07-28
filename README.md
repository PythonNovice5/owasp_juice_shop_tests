# OWASP Juice Shop Test Suite

## Description
This project is a test suite for the OWASP Juice Shop, designed to ensure that key functionalities of the application work as expected. The test suite includes cases for verifying pagination, items per page, language changes, login functionality, and more.

## Building and Running the Application with Docker

Using Docker is a straightforward way to set up and run the OWASP Juice Shop application. Follow these steps to get it running:

### Prerequisites
- **Docker**: Ensure Docker is installed on your machine. You can download it from [docker.com](https://www.docker.com/products/docker-desktop).

### Instructions

1. **Install Docker (If not installed)**: Follow the installation instructions for your operating system from the [Docker website](https://docs.docker.com/get-docker/).

2. **Pull the Juice Shop Docker Image**:
   ```bash
   docker pull bkimminich/juice-shop
   ```

3. **Run the Juice Shop Docker Container**:
   ```bash
   docker run -d --rm --name juice-shop -p 3000:3000 bkimminich/juice-shop
   ```

   This command runs the Juice Shop container and maps port 3000 on your host machine to port 3000 in the container.

4. **Access the Application**:
   - Open your web browser and navigate to [http://localhost:3000](http://localhost:3000) if you are using Docker natively.
   - If you are using Docker Machine on macOS or Windows, browse to [http://192.168.99.100:3000](http://192.168.99.100:3000).

## Installation of Test Suite

### Prerequisites
- **Python**: Ensure Python is installed. You can download it from [python.org](https://www.python.org/).
- **Git**: Required for cloning the test suite repository.

### Instructions

1. **Clone the Test Suite Repository**:
   ```bash
   git clone https://github.com/PythonNovice5/owasp_juice_shop_tests.git
   ```

2. **Navigate to the Test Suite Directory**:
   ```bash
   cd owasp_juice_shop_tests
   ```
3. **Set up Virtual env and install the dependencies [Windows]**:
   ```bash
   python -m venv venv 
   venv\Scripts\activate.bat
   ```
   **Set up Virtual env and install the dependencies [Linux]**:
   ```bash
   python3 -m venv venv 
   source venv/bin/activate
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
## Security Scanning with OWASP ZAP

You can use OWASP ZAP to perform security scans on your application. Here are the different types of scans you can run:

### 1. Baseline Scan

This scan runs the ZAP spider for 1 minute and then waits for the passive scanning to complete before reporting the results.

```bash
docker run --rm --user root -v $(pwd):/zap/wrk/:rw --net host -t zaproxy/zap-weekly zap-baseline.py -r report_baseline.html -t http://localhost:3000
```

### 2. API Scan

This scan performs scans against APIs defined by OpenAPI.

```bash
docker run --rm --user root -v $(pwd):/zap/wrk/:rw --net host -t zaproxy/zap-weekly zap-api-scan.py -f openapi -r report_api.html -t http://localhost:3000
```

### 3. Full Scan

This scan performs a full scan (without any time limit) and includes actual attacks.

```bash
docker run --rm --user root -v $(pwd):/zap/wrk/:rw --net host -t zaproxy/zap-weekly zap-full-scan.py -r report_fullscan.html -t http://localhost:3000
```
**Locate the HTML Reports**:
   The reports will be saved in your current working directory as `report.html`, `report_baseline.html`, `report_api.html`, and `report_fullscan.html`.

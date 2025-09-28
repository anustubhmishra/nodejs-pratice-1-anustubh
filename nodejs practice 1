
const readline = require('readline');

// Create readline interface
const rl = readline.createInterface({
    input: process.stdin,
    output: process.stdout
});

// Employee array to store employee data
let employees = [
    { name: 'Alice', id: 'E101' },
    { name: 'Bob', id: 'E102' },
    { name: 'Charlie', id: 'E103' }
];

// Function to display the main menu
function showMenu() {
    console.log('\nEmployee Management System');
    console.log('1. Add Employee');
    console.log('2. List Employees');
    console.log('3. Remove Employee');
    console.log('4. Exit');
    console.log('');
}

// Function to list all employees
function listEmployees() {
    console.log('\nEmployee List:');
    if (employees.length === 0) {
        console.log('No employees found.');
    } else {
        employees.forEach((employee, index) => {
            console.log(`${index + 1}. Name: ${employee.name}, ID: ${employee.id}`);
        });
    }
}

// Function to add a new employee
function addEmployee() {
    rl.question('Enter employee name: ', (name) => {
        rl.question('Enter employee ID: ', (id) => {
            // Check if employee ID already exists
            const existingEmployee = employees.find(emp => emp.id === id);
            if (existingEmployee) {
                console.log(`Error: Employee with ID ${id} already exists.`);
            } else {
                employees.push({ name: name, id: id });
                console.log(`Employee ${name} (ID: ${id}) added successfully.`);
            }
            showMenuAndGetChoice();
        });
    });
}

// Function to remove an employee by ID
function removeEmployee() {
    rl.question('Enter employee ID to remove: ', (id) => {
        const employeeIndex = employees.findIndex(emp => emp.id === id);
        if (employeeIndex !== -1) {
            const removedEmployee = employees[employeeIndex];
            employees.splice(employeeIndex, 1);
            console.log(`Employee ${removedEmployee.name} (ID: ${id}) removed successfully.`);
        } else {
            console.log(`Error: Employee with ID ${id} not found.`);
        }
        showMenuAndGetChoice();
    });
}

// Function to handle user choice
function handleChoice(choice) {
    switch (choice) {
        case '1':
            addEmployee();
            break;
        case '2':
            listEmployees();
            showMenuAndGetChoice();
            break;
        case '3':
            removeEmployee();
            break;
        case '4':
            console.log('Goodbye!');
            rl.close();
            break;
        default:
            console.log('Invalid choice. Please enter a number between 1 and 4.');
            showMenuAndGetChoice();
            break;
    }
}

// Function to show menu and get user choice
function showMenuAndGetChoice() {
    showMenu();
    rl.question('Enter your choice: ', (choice) => {
        handleChoice(choice);
    });
}

// Start the application
console.log('Welcome to the Employee Management System!');
showMenuAndGetChoice();

// Handle process termination
process.on('SIGINT', () => {
    console.log('\nApplication terminated by user.');
    rl.close();
    process.exit(0);
});

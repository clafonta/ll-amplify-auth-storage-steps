# Getting Started with NextJS

NextJS

## Installation

Before we begin, make sure you have Node.js installed on your system. Then, follow these steps to create a new React application:

1. Open your terminal.
2. Run the following command to create a new React app:

   ```bash
   npx create-react-app my-react-app

Then

   ```typescript
   interface User {
  id: number;
  name: string;
  email: string;
}

function greetUser(user: User): string {
  return `Hello, ${user.name}! Your email is ${user.email}.`;
}

const newUser: User = {
  id: 1,
  name: "Alice",
  email: "alice@example.com"
};

console.log(greetUser(newUser));

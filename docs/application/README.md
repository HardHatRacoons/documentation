# Application Documentation

## How to Run

1. To get started, clone the repository by running

```bash
git clone git@github.com:HardHatRacoons/rustle-rustle-react.git
```

2. Then install all of the dependencies with:

```bash
npm i
```

3. Follow instructions from [Local Hosting Docs](/application/local_hosting.md) to set up AWS Amplify resources locally.

4. Lastly, run the website locally with:

```bash
npm run dev
```

5. The application should be accessible at `http://localhost:4321` by default.

---

## The Tech Stack
### Main Tools
#### ReactJS

React JS is the main tool used for building the dynamic graphical user interface. It is standard industry best-practice. 

#### Vite

Vite is the build tool/development server used serve react code. It is highly effecient and offers a variety of useful features.

#### TailwindCSS

TailwindCSS is a quick css styling tool to speed up development and ensure style consistency.

### Supplementary Libraries
#### React-Router

React router was used for relatively lightweight client side routing that doesn't requre full page reloads. 

#### React-Icons

React icons were used for styling the web app with premade icon (svg) libraries.

#### PDFJS-dist

This is a pdf.js distribution used to render pdfs in the browser.

#### AGGrid

AGGrid is a powerful tool for rendering large and complex data sets in a grid. It is used for rendering a large amount of steel structure data in a table with additional functionality (sorting, filtering, pagination).

### Testing Libraries
#### React Testing Library (RTL)

RTL was used to write test code for the react app to make sure behavior stays consistent and expected. It closely mimicks the browser environment and user experience.

#### Jest

Jest was used to run the tests and give code coverage metrics as well as provide mocking support.

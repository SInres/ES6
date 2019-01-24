# ES6+
Description and differences in the new ES6+ in JavaScript syntax

1. Domyślne wartości

        const adrian = 'adrian';

        /* Stary sposób */
        function getName(name) {
            var name = name || 'Adrian';
            console.log(`My name is ${name}`);
        }

        getName();


        /* Nowy sposób */
        function getName(name = 'Adrian') {
            console.log(`My name is ${name}`);
        }

        getName();
        getName(adrian);
        getName('Paula');
    
2. Nowe stringi

        /* Stary sposób */
    
        const myNewStr = 'Lorem ipsum dolor sit amet \n'
        + 'consectetur adipisicing elit. Cum accusamus \n'
        + 'recusandae voluptatum, consequatur alias repudiandae \n'
        + 'dolore distinctio sed. Magnam molestiae officiis consectetur';

        console.log(myNewStr);


        /* Nowy sposób */

        const myNewStr2 = `Lorem ipsum dolor sit amet
            consectetur adipisicing elit. Cum accusamus
            recusandae voluptatum, consequatur alias repudiandae
            dolore distinctio sed. Magnam molestiae officiis consectetur`;

        console.log(myNewStr2);

3. Drugą fajną zaletą nowych stringów jest dodawanie zmiennych wewnątrz stringów */

        /* Stary sposób */

        const adrian1 = 'Adrian';
        console.log('My name is ' + adrian1);


        /* Nowy sposób */

        const adrian2 = 'Adrian';
        console.log(`My name is ${adrian2}`);

4. Destructuring - pozwala nam na wyciąganie zmiennych z objektów lub tablic bezpośrednio 
    do osobnych zmiennych, które potem możemy sobie wykorzystywać w kodzie

        /* 1: Wyciąganie do zmiennych */
        

        /* Stary sposób */

        const myObject = {
            name: 'Adrian',
            job: 'Programmer',
            formerJob: 'Specialist IT',
            age: '25',
        };

        var name = myObject.name;
        console.log(name);
        

        /* Nowy sposób */

        const {age} = myObject;
        console.log(age);
        

        /* 2: Wyciąganie w funkcji */
        

        /* Stary sposób */
        function myJob(personalData) {
            console.log(`My name is ${personalData.name} and i'm a ${personalData.job}`);
        }

        myJob(myObject);
        

        /* Lpeszy sposób */
        function myJob2(personalData) {
            const { name, job } = personalData;
            console.log(`My name is ${name} and i'm a ${job}`);
        }

        myJob2(myObject);
        

        /* Najlepszy sposób */
        function myJob3({name, job}) {
            console.log(`My name is ${name} and i'm a ${job}`);
        }

        myJob3(myObject);


        /* 3: Zagniezdzone obiekty */

        const myObjectDetails = {
            name: 'Adrian',
            job: 'programmer',
            formerJobs: {
                first: 'electro fitter',
                second: 'specialist it',
                recent: 'programmer',
            },
            age: '25',
        }
        

        /* Stary sposób */
        function getFirstJob(personalData) {
            console.log(`I was a ${personalData.formerJobs.first} back in 2016.`);
        }
        getFirstJob(myObjectDetails);
        

        /* Lepszy sposób */
        function getFirstJob2({formerJobs: {first} }) {
            console.log(`I was a ${first} back in 2016.`);
        }
        getFirstJob(myObjectDetails);
        

        /* 4: Destructuring tablic */

        const names = ['Adrian', 'Paulina', 'Basia'];
        const [first, second] = names;
        console.log(first, second);

5. Arrow functions - zrewolucjonizował to jak piszę i korzysta się z JavaScriptu :-)
        
        /* Stary sposób */
        function returnName(name) {
            return `My name is ${name}`;
        }
        

        /* Lepszy sposób */
        const returnName2 = (name) => {
            return `My name is ${name}`;
        }
        

        /* Najlepszy sposób */
        const returnName3 = (name) => `My name is ${name}`;

        console.log(returnName('Adrian'));
        console.log(returnName2('Paulina'));
        console.log(returnName3('Pies'));

5. ECM - ECMAScript Modules

        /* Stary sposób */
        const adrianDir = require('./adrian.js');
        console.log(adrianDir);

        /* Named export */
        import { adrian } from './newAdrian';
        console.log(adrian);

        /* Default export */
        // W ten sposób przpisujemy nową nazwę zmiennej NameOfAdrian do importowanej zmiennej defaultowej
        import NameOfAdrian from './defaultAdrian';
        console.log(NameOfAdrian);

        // Lub
        import AdrianZawada from './defaultAdrian';
        console.log(AdrianZawada);

        W ten sposób do zmiennej importowanej o nazwie adrian przypisaliśmy nową nazwę zmiennej AdrianZawada

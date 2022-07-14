# Автотесты с использованием готовых фрагментов кода (Snippets)
`http://162.55.220.72:5005/first` (метод запроса - GET)
1. Отправить запрос.
2. Статус код 200.
```js
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```
3. Проверить, что в body приходит правильный string.
```js
pm.test("Body matches string", function () {
    pm.expect(pm.response.text()).to.include("This is the first responce from server!");
});
```
---
`http://162.55.220.72:5005/user_info_3` (метод запроса - POST)
1. Отправить запрос.
2. Статус код 200.
```js
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```
3. Спарсить response body в json.
```js
let jsonData = pm.response.json();
```
4. Проверить, что name в ответе равно name s request (name вбить руками).
```js
pm.test("Check name = Eduard", function () {
    pm.expect(jsonData.name).to.eql("Eduard");
});
```
5. Проверить, что age в ответе равно age s request (age вбить руками).
```js
pm.test("Check age = 33", function () {
    pm.expect(jsonData.age).to.eql("33");
});
```
6. Проверить, что salary в ответе равно salary s request (salary вбить руками).
```js
pm.test("Check salary = 3000", function () {
    pm.expect(jsonData.salary).to.eql(3000);
});
```
7. Спарсить request.
```js
let reqData = request.data;
```
8. Проверить, что name в ответе равно name s request (name забрать из request).
```js
pm.test("Check name: response = request", function () {
    pm.expect(jsonData.name).to.eql(reqData.name);
});
```
9. Проверить, что age в ответе равно age s request (age забрать из request).
```js
pm.test("Check age: response = request", function () {
    pm.expect(jsonData.age).to.eql(reqData.age);
});
```
10. Проверить, что salary в ответе равно salary s request (salary забрать из request).
```js
pm.test("Check salary: response = request", function () {
    pm.expect(jsonData.salary).to.eql(+reqData.salary);
    // "+" преобразует строку в число (string to integer).
});
```
11. Вывести в консоль параметр family из response.
```js
console.log(jsonData.family);
```
12. Проверить что u_salary_1_5_year в ответе равно salary*4 (salary забрать из request).
```js
let resp_salary_1_5 = jsonData.family.u_salary_1_5_year;
let req_salary_1_5 = reqData.salary * 4;
pm.test("Salary after 1.5 years = 12000", function () {
    pm.expect(req_salary_1_5).to.eql(resp_salary_1_5);
});
```
---
`http://162.55.220.72:5005/object_info_3` (метод запроса - GET)
1. Отправить запрос.
2. Статус код 200.
```js
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```
3. Спарсить response body в json.
```js
let jsonData = pm.response.json();
```
4. Спарсить request.
```js
let reqData = pm.request.url.query.toObject();
```
5. Проверить, что name в ответе равно name s request (name забрать из request).
```js
pm.test("Check name: response = request", function () {
    pm.expect(jsonData.name).to.eql(reqData.name);
});
```
6. Проверить, что age в ответе равно age s request (age забрать из request).
```js
pm.test("Check age: response = request", function () {
    pm.expect(jsonData.age).to.eql(reqData.age);
});
```
7. Проверить, что salary в ответе равно salary s request (salary забрать из request).
```js
pm.test("Check salary: response = request", function () {
    pm.expect(jsonData.salary).to.eql(+reqData.salary);
    // "+" преобразует строку в число (string to integer).
});
```
8. Вывести в консоль параметр family из response.
```js
console.log(jsonData.family);
```
9. Проверить, что у параметра dog есть параметры name.
```js
pm.test("Dog has a name", function () {
    pm.expect(jsonData.family.pets.dog).to.have.property("name");
});
```
10. Проверить, что у параметра dog есть параметры age.
```js
pm.test("Dog has a age", function () {
    pm.expect(jsonData.family.pets.dog).to.have.property("age");
});
```
11. Проверить, что параметр name имеет значение Luky.
```js
pm.test("Dog's name is Luky", function () {
    pm.expect(jsonData.family.pets.dog.name).to.eql("Luky");
});
```
12. Проверить, что параметр age имеет значение 4.
```js
pm.test("Dog's age = 4", function () {
    pm.expect(jsonData.family.pets.dog.age).to.eql(4);
});
```
---
`http://162.55.220.72:5005/object_info_4` (метод запроса - GET)
1. Отправить запрос.
2. Статус код 200.
```js
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```
3. Спарсить response body в json.
```js
let jsonData = pm.response.json();
```
4. Спарсить request.
```js
let reqData = pm.request.url.query.toObject();
```
5. Проверить, что name в ответе равно name s request (name забрать из request).
```js
pm.test("Check name: response = request", function () {
    pm.expect(jsonData.name).to.eql(reqData.name);
});
```
6. Проверить, что age в ответе равно age из request (age забрать из request).
```js
pm.test("Check age: response = request", function () {
    pm.expect(jsonData.age).to.eql(+reqData.age);
    // "+" преобразует строку в число (string to integer).
});
```
7. Вывести в консоль параметр salary из request.
```js
console.log(reqData.salary)
```
8. Вывести в консоль параметр salary из response.
```js
console.log(jsonData.salary)
```
9. Вывести в консоль 0-й элемент параметра salary из response.
```js
console.log(jsonData.salary[0])
```
10. Вывести в консоль 1-й элемент параметра salary параметр salary из response.
```js
console.log(jsonData.salary[1])
```
11. Вывести в консоль 2-й элемент параметра salary параметр salary из response.
```js
console.log(jsonData.salary[2])
```
12. Проверить, что 0-й элемент параметра salary равен salary из request (salary забрать из request).
```js
pm.test("Check response salary [0] = request salary", function () {
    pm.expect(jsonData.salary[0]).to.eql+(reqData.salary);
});
```
13. Проверить, что 1-й элемент параметра salary равен salary*2 из request (salary забрать из request).
```js
let req_salary_6000 = reqData.salary * 2;
pm.test("Check response salary [1] = request salary*2", function () {
    pm.expect(jsonData.salary[1]).to.eql+(req_salary_6000);
});
```
14. Проверить, что 2-й элемент параметра salary равен salary*3 из request (salary забрать из request).
```js
let req_salary_9000 = reqData.salary * 3;
pm.test("Check response salary [2] = request salary*2", function () {
    pm.expect(jsonData.salary[2]).to.eql+(req_salary_6000);
});
```
15. Создать в окружении переменную name.
16. Создать в окружении переменную age.
17. Создать в окружении переменную salary.
18. Передать в окружение переменную name
```js
pm.environment.set("name", jsonData.name);
```
19. Передать в окружение переменную age
```js
pm.environment.set("age", jsonData.age);
```
20. Передать в окружение переменную salary
```js
pm.environment.set("salary", jsonData.salary[0]);
```
21. Написать цикл который выведет в консоль по порядку элементы списка из параметра salary.
```js
for (let i = 0; i < jsonData.salary.length; i++) {
  console.log("Element of list from salary " + jsonData.salary[i]);
}
```
---
`http://162.55.220.72:5005/user_info_2` (метод запроса - POST)
1. Вставить параметр salary из окружения в request.
2. Вставить параметр age из окружения в age.
3. Вставить параметр name из окружения в name.
+ Body: {{значение}} - данные подтягиваются из окружения
4. Отправить запрос.
5. Статус код 200.
```js
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```
6. Спарсить response body в json.
```js
let jsonData = pm.response.json();
```
7. Спарсить request.
```js
let reqData = request.data;
```
8. Проверить, что json response имеет параметр start_qa_salary.
```js
pm.test("Check response has the parameter start qa salary", () => {
    pm.expect(jsonData).to.have.property("start_qa_salary");
});
```
9. Проверить, что json response имеет параметр qa_salary_after_6_months.
```js
pm.test("Check response has the parameter qa salary after 6 months", () => {
    pm.expect(jsonData).to.have.property("qa_salary_after_6_months");
});
```
10. Проверить, что json response имеет параметр qa_salary_after_12_months.
```js
pm.test("Check response has the parameter qa salary after 12 months", () => {
    pm.expect(jsonData).to.have.property("qa_salary_after_12_months");
});
```
11. Проверить, что json response имеет параметр qa_salary_after_1.5_year.
```js
pm.test("Check response has the parameter qa salary after 1.5 year", () => {
    pm.expect(jsonData).to.have.property("qa_salary_after_1.5_year");
});
```
12. Проверить, что json response имеет параметр qa_salary_after_3.5_years.
```js
pm.test("Check response has the parameter qa salary after 3.5 years", () => {
    pm.expect(jsonData).to.have.property("qa_salary_after_3.5_years");
});
```
13. Проверить, что json response имеет параметр person.
```js
pm.test("Check response has the parameter person", () => {
    pm.expect(jsonData).to.have.property("person");
});
```
14. Проверить, что параметр start_qa_salary равен salary из request (salary забрать из request).
```js
pm.test("Check start qa salary = request salary", () => {
    pm.expect(jsonData.start_qa_salary).to.eql+(reqData.salary);
});
```
15. Проверить, что параметр qa_salary_after_6_months равен salary*2 из request (salary забрать из request).
```js
let req_salary_6000 = reqData.salary * 2;
pm.test("Check qa salary after 6 months = request salary*2", () => {
    pm.expect(jsonData.qa_salary_after_6_months).to.eql+(req_salary_6000);
});
```
16. Проверить, что параметр qa_salary_after_12_months равен salary*2.7 из request (salary забрать из request).
```js
let req_salary_8100 = reqData.salary * 2.7;
pm.test("Check qa salary after 12 months = request salary*2.7", () => {
    pm.expect(jsonData.qa_salary_after_12_months).to.eql+(req_salary_8100);
});
```
17. Проверить, что параметр qa_salary_after_1.5_year равен salary*3.3 из request (salary забрать из request).
```js
let req_salary_9900 = reqData.salary * 3.3;
pm.test("Check qa salary qa salary after 1.5 year = request salary*3.3", () => {
    pm.expect(["jsonData.qa_salary_after_1.5_year"]).to.eql+(req_salary_9900);
});
```
18. Проверить, что параметр qa_salary_after_3.5_years равен salary*3.8 из request (salary забрать из request).
```js
let req_salary_11400 = reqData.salary * 3.8;
pm.test("Check qa salary after 3.5 years = request salary*3.8", () => {
    pm.expect(jsonData.qa_salary_after_12_months).to.eql+(req_salary_11400);
});
```
19. Проверить, что в параметре person, 1-й элемент из u_name равен salary из request (salary забрать из request).
```js
pm.test("Check 1-st element u_name from person = request salary", () => {
    pm.expect(jsonData.person.u_name[1]).to.eql+(reqData.salary);
});
```
20. Проверить, что что параметр u_age равен age из request (age забрать из request).
```js
pm.test("Check u age = request age", () => {
    pm.expect(jsonData.u_name).to.eql+(reqData.age);
});
```
21. Проверить, что параметр u_salary_5_years равен salary*4.2 из request (salary забрать из request).
```js
let req_salary_12600 = reqData.salary * 4.2;
pm.test("Check u salary 5 years = request salary*4.2", () => {
    pm.expect(jsonData.u_salary_5_years).to.eql+(req_salary_12600);
});
```
22. Написать цикл который выведет в консоль по порядку элементы списка из параметра person.
```js
for (let i = 0; i < jsonData.person.u_name.length; i++) {
  console.log("Element of list from person " + jsonData.person.u_name[i]);
}
```

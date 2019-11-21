**this jwt encoder is used to automate token generation for lambda api call requests which require unique token for each call.**

the following needs to be added to postman env pre required script:
```
pm.sendRequest({
url: "http://localhost:3000/login",
method: 'POST',
header: {
'Accept': 'application/json',
'Content-Type': 'application/x-www-form-urlencoded'
},
body: {
mode: 'urlencoded',
urlencoded: [
{key: "name", value: [username], disabled: false},
{key: "password", value: [password], disabled: false}
]
}
}, function (err, res) {
pm.globals.set("_TOKEN", res.json().token);
});
```
**Note: username password need to be updated, plus following values are needed under .env file (u & p + jwt payload and secret-key):**
```
NAME=
PASSWORD=
SUB=
ISS=
AUD=
FIID=
CUSTID=
EXP=
SECRET_KEY=
```

**Steps:**
```
once cloned,
create .evn file, 
install dependencies,
add postman env pre-required script then
npm start,
then use _TOKEN which is set under global variables for each call.
```

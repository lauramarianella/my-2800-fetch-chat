http://wakaworkshops.surge.sh/workshop/fetch-chat/slides/0

index.html: as before, 2 forms for signup and for login.
chat.html:

<html
<ul id=”msg-list”></ul>
<form action=”/messages” method=”POST” enctype=”multipart/form-data”
<input text name message
<input submit
<script src=”/static/app.js”></script>

app.js
let fetchAndUpdate = async () => {
let response = await fetch(‘/messages’)
let respondeBody = await response.text()
let parsed = JSON.parse(responseBody)
let msgListUL = document.getElementById(‘msg-list’);
msgList.innerHTML = “”
parsed.forEach(elem => {
let li = document.createElement(“li”);
li.innerText = elem.user + “: ” + elem.msg
msgListUL.append(li);
})
}

fetchAndUpdate();
setInterval(fetchAndUpdate, 500)

server.js
let express = require
app
cookieOarser = req(“cookie-parser
multer
upload = multer()
app.use(cookieParser())

passwordsAssoc = {}
sessions ={}
messages = []

app.use(/static, express.static(dirname+/public))

app.get(“/”) res.sendFile(\_\_dirname + /public/index)

app.post(/messages, upload.none(), function){
messages.push({user: cookies.sid, msg: req.body })
res.sendFile(bla bla + /public+chat.html/)
}

app.get(/messages,
res.send(JSON.stringify(messages))
)

app.post(/signup)
app.post(/login){
generate cookie
res.cookie(‘key’,value)
res.sendFile(chat page)
}

app.listen(3000)

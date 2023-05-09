<img src="../../Image/frontend-dev.png" style="object-fit: cover" width="100%"/>

<br>
<br>


# ⚒️  `DiscordBot of MyInfo Project`

<br>

<img src="./Image/myinfo_4.png" style="object-fit: cover" width="400px" height="200px"/>

<br>


* **정의**
* **기능**
* **컴포넌트**

<br>


> 정의

```
MyInfo 에서 
웹 개발자 소개 페이지기 때문에

의뢰인의 요청을 고려해서
구현한 Discord bot 을 연결한
요청 POST API
```
<br>
<br>

> 기능

```javascript
discord_url = ...

// Col 별로 Contents 를 분리
def message_column(contents):
    prevCols = ['name','tel','email','request']
    nextCols = ['🏷️\n이름\t\t\t','번호\t\t\t','이메일\t\t','\n요청사항\t\n']
    
    for i in range(len(prevCols)):
        contents = contents.replace(prevCols[i], nextCols[i])

    return contents

// Contents Formatting
def message_format(contents):
    contents = message_column(contents)
    return contents.replace('{','').replace('}','').replace('\'','').replace(', ','\n').replace(':', '▶️ ')

// Contents 연결된 Discord 로 Send
def send_message(datas):
    line = "\nㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ\n"
    data = {'content':'{}{}'.format(line,message_format(str(datas)))}
    print(datas)
    response = requests.post(discord_url, data=data)
    print(response)

```
<br>
<br>

> 컴포넌트

```javascript
... 

<Modal show={show} onHide={handleClose}>
    <Modal.Header>
      <Modal.Title>Request</Modal.Title>
    </Modal.Header>
    <Modal.Body>
      If you have any requests for me, please contact me here.
      <div class="mb-3">
        <label
          for="recipient-name"
          class="col-form-label"
          className={styles.modal_lebel}
        >
          Username:
        </label>
        <input
          type="text"
          class="form-control"
          id="recipient-name"
          name="name"
          onChange={onChangeMessage}
        />
      </div>
      <div class="mb-3">
        <label for="tel-text" class="col-form-label">
          tel:
        </label>
        <input
          type="text"
          class="form-control"
          id="recipient-tel"
          name="tel"
          placeholder="- 없이 연락처를 입력해주세요. (선택)"
          onChange={onChangeMessage}
        />
      </div>
      <div class="mb-3">
        <label for="email-text" class="col-form-label">
          Email:
        </label>
        <input
          type="text"
          class="form-control"
          id="recipient-email"
          name="email"
          onChange={onChangeMessage}
        />
      </div>
      <div class="mb-3">
        <label for="message-text" class="col-form-label">
          Message:
        </label>
        <textarea
          class="form-control"
          className={styles.modal_area}
          id="message-text"
          name="request"
          onChange={onChangeMessage}
        ></textarea>
      </div>
    </Modal.Body>
    <Modal.Footer>
      <Button
        className="btn_close"
        variant="secondary"
        onClick={handleClose}
      >
        닫기
      </Button>
      <Button variant="btn btn-primary" onClick={sendMessage}>
        Send message
      </Button>
    </Modal.Footer>
  </Modal>
```
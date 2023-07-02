<img src="../Image/testcodeLogo.jpeg" style="object-fit: cover" width="100%"/>

<br>
<br>


# ⚒️  `E2E 테스트를 알아보자 (at React)`

<br>


* **정의**
* **장점**
* **방법**
* **사용코드**
* **추가 팁**

<br>

> 정의

<br>

```
애플리케이션의 전체 플로우를 테스트

실제 사용자가 애플리케이션을 사용하는 것과 
유사한 환경에서 동작을 검증하는 테스트

E2E 테스트는 사용자 인터페이스와 상호작용

여러 컴포넌트, 서비스, API 등을 포함한 
애플리케이션의 여러 부분을 통합적으로 테스트
```

<br><br>

> 장점


<br>

&nbsp;&nbsp;&nbsp;&nbsp;`전체 플로우 테스트`
```
애플리케이션의 전체 플로우를 테스트

사용자의 실제 경험을 
재현하고 문제를 식별 가능
```
<br>

&nbsp;&nbsp;&nbsp;&nbsp;`실제 환경 검증`
```
실제 환경에서 애플리케이션을 테스트

배포 전에 애플리케이션이 
예상대로 동작하는지 확인 가능
```

<br>

&nbsp;&nbsp;&nbsp;&nbsp;`사용자 관점 검증`
```
사용자의 관점에서 애플리케이션을 테스트

사용자가 마주할 수 있는 문제를 미리 감지 가능
```

<br>

&nbsp;&nbsp;&nbsp;&nbsp;`버그 감소`
```
다양한 기능을 통합하여 테스트

버그 발생 가능성 줄이기 가능
```

<br><br>

> 방법

<br>

```
E2E 테스트를 작성하는 방법은 
다양한 도구를 사용 가능 

대표적인 도구로는 
Cypress, Puppeteer, Selenium 등이 존재
```


<br><br>

> 사용코드

<br>

&nbsp;&nbsp;&nbsp;&nbsp;`React Testing Library E2E Test Example`
```javascript
import { render, fireEvent, screen } from '@testing-library/react';
import App from './App';

test('complete sign up flow', () => {
  // 애플리케이션 렌더링
  render(<App />);

  // 로그인 페이지에서 이메일 입력
  fireEvent.change(screen.getByLabelText('Email'), { target: { value: 'test@example.com' } });
  
  // 로그인 페이지에서 비밀번호 입력
  fireEvent.change(screen.getByLabelText('Password'), { target: { value: 'password123' } });
  
  // 로그인 버튼 클릭
  fireEvent.click(screen.getByRole('button', { name: 'Sign In' }));

  // 대시보드 페이지로 이동한 후 상태 확인
  expect(screen.getByText('Welcome to the Dashboard')).toBeInTheDocument();
});
```

<br>

&nbsp;&nbsp;&nbsp;&nbsp;`Cypress E2E Test Example`<br>
&nbsp;&nbsp;&nbsp;&nbsp; 사용자의 브라우저 동작을 시뮬레이션하여 테스트
```javascript
describe('Complete Sign Up Flow', () => {
  it('should sign up successfully', () => {
    // Cypress 코드 작성
    cy.visit('/');
  
    cy.get('input[name="email"]').type('test@example.com');
    cy.get('input[name="password"]').type('password123');
  
    cy.get('button[type="submit"]').click();
  
    cy.contains('Welcome to the Dashboard').should('be.visible');
  });
});

```
<br>

&nbsp;&nbsp;&nbsp;&nbsp;`Puppeteer`
<br>&nbsp;&nbsp;&nbsp;&nbsp;웹 브라우저를 자동화하여 테스트 가능

<br>
<br>

> 추가 팁

```
테스트 시나리오를 정의하고 테스트 케이스를 작성

어떤 동작을 테스트할지, 
어떤 결과를 예상하는지 등을 
명확하게 정의

테스트 환경을 설정하고 테스트 데이터를 준비

필요한 데이터를 생성하거나 
모의 데이터를 사용하여 테스트 환경을 구성


테스트 결과를 확인하기 위해 
예상 결과와 실제 결과를 비교

테스트 결과가 예상과 일치하는지 확인
테스트의 유효성을 검증


테스트 코드를 유지보수하고 
지속적으로 개선

애플리케이션의 변경 사항에 맞게 
테스트 코드를 업데이트하고, 
신뢰성을 높이기 위해 테스트 커버리지를 확장
```

<br><br>

> 설명

- `사용자 흐름 정의`
<br>
- `다양한 시나리오와 엣지 케이스 테스트를 고려`


```
먼저 테스트해야 하는 사용자 흐름을 이해

여기에는 일반 사용자가 애플리케이션에서 
수행할 수 있는 작업을 이해하는 것이 포함

예를 들어 전자상거래 사이트를 테스트하는 경우 
일반적인 흐름은 다음과 같음
```
ex ) 

- `사이트 열기`
- `제품 검색`
- `장바구니에 담기`
- `결제 진행`
- `결제 정보 작성`
- `구매 확인`
<br>
```javascript
describe('E-commerce user flow', function() {
  it('completes a purchase', function() {
    // Open the site
    cy.visit('https://www.your-ecommerce-site.com')

    // Search for a product
    cy.get('.search-bar').type('Awesome Product{enter}')

    // Choose the product from the list
    cy.get('.product-list')
      .contains('Awesome Product')
      .click()

    // Add it to the cart
    cy.get('.add-to-cart').click()

    // Proceed to checkout
    cy.get('.checkout').click()

    // Fill out payment information
    cy.get('.payment-info')
      .within(() => {
        cy.get('input[name=card-number]').type('4111111111111111')
        cy.get('input[name=expiry-date]').type('12/2025')
        cy.get('input[name=cvv]').type('123')
      })

    // Confirm purchase
    cy.get('.confirm-purchase').click()

    // Check for a successful purchase message
    cy.get('.purchase-success').should('contain', 'Thank you for your purchase!')
  })
})
```
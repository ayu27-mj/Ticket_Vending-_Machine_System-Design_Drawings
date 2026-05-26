```mermaid
sequenceDiagram
    participant Alice
    participant Bob
    Alice->>John: Hello John, how are you?
    loop HealthCheck
        John->>John: Fight against hypochondria
    end
    Note right of John: Rational thoughts <br/>prevail!
    John-->>Alice: Great!
    John->>Bob: How about you?
    Bob-->>John: Jolly good!


    actor User
    participant Main
    participant TicketVender
    participant Item
    participant Cart
    participant CartItem
    Main ->> TicketVender:new
    TicketVender ->> Item:new
    Note right of Item:商品の個数分生成する
    TicketVender ->> Cart:new
    Main ->>TicketVender:showItems()
    loop 
    User ->>Main:商品番号入力
    Main ->> TicketVender:addItemToCart(id)
    TicketVender ->> Cart:addItem(item)
    Cart ->> CartItem:new
    end
    Note right of CartItem:同じ商品がある場合<br>は、newではなく数<br>量を変更する。
    Main ->> TicketVender:showCartItems()
    TicketVender ->> Cart:getCartItems()
    TicketVender ->> Cart:getTotalPrice()
    User ->> Main:投入金額を入力
    Main ->> TicketVender:calcChange(payment)
    TicketVender ->> Cart:getTotalPrice()
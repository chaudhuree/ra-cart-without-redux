## Details how to follow the code
1. create context.js

- in create context create AppContext

  

```

const AppContext = React.createContext()

```

  

- create AppProvider

-in app provider create useReducer

  

```

const [state, dispatch] = useReducer(reducer, initialState)

```

  

initial state is,

  

```

const initialState = {

loading: false,

cart: cartItems,

total: 0,

amount: 0,

}

```

  

- initially cart has static value form data.js file,next in dispatch we will replace static data with dynamic using fetchData function.

where we have dispatch,

  

```

({type: 'DISPLAY_ITEMS', payload: cart})

```

  

2. we have two dispatch in this context one is for fetching data. and another is for calculating amount and total cart item while cart value change in state.

  

```

in second useEffect

[state.cart]

```

  

3. we have separated the reducer function in reducer.js file.

in it all the functionality is written.

in it, state holds the value of initialState and action holds the value of dispatch.

  

4. now we have create different functions in the context.js file. like, remove, increase, decrease, clearCart, toggleAmount.

5. we have passed it through the value prop of AppProvider. so that we can use it in cartItem component. and navbar component.etc..

6. we have also created a useGlobalContext function to use the context in other components.so that we can have the value in every other page.

> describe the reducer function in reducer.js file.

7. we have reducer function which have two props, state and action.

8. state holds the initial state value and action holds the value of dispatch.

9. first we have CLEAR_CART case, which will clear the cart. just set the cart to empty array.

10. next we have REMOVE case, which will remove the item from the cart. we have used filter method to remove the item from the cart.

11. then we have INCREASE case, which will increase the quantity of the item in the cart. we have used map method to increase the quantity of the item. we will first have a tempCart which will hold the value of cart. then we will map through the tempCart and if the id of the item matches with the id of the item in the cart then we will increase the quantity of that item by 1. then finally return the tempCart by assigning it to the cart.

12. then we have DECREASE case, which will decrease the quantity of the item in the cart. we have used map method to decrease the quantity of the item. we will first have a tempCart which will hold the value of cart. then we will map through the tempCart and if the id of the item matches with the id of the item in the cart then we will decrease the quantity of that item by 1.after mapping this we will have a new array. then by chainig array method we will filter through the array and chaeck if there has any item which amount is zero. then will will filter out that item. then finally return the tempCart by assigning it to the cart.

  

13.(this is optional it will work if we remove increase or decrease functionality)we have TOGGLE_AMOUNT case, which will increase or decrease the quantity of the item in the cart. we have used map method to increase or decrease the quantity of the item. we will first have a tempCart which will hold the value of cart. then we will map through the tempCart and if the id of the item matches with the id of the item in the cart then we will increase or decrease the quantity of that item by 1. then finally return the tempCart by assigning it to the cart.

  

14. then we have DISPLAY_ITEMS case, which will display the items in the cart. we will assign the payload to the cart. then we will return the state. by this way we will dinamically change the cart value.

15. finally we have GET_TOTALS case,it will return two value one is total and another is amount. we will use reduce method to get the total and amount.

1. reducer has two parameter, first is accumulator and another is currentValue.

2. accumulator is the second parameter of the reduce method. it will hold the value which we will return from the reduce method.

3. if we have accumulator as 0 then it will return 0. if we have accumulator as an object then reducer function will return an object.

4. in this case we have accumulator as an object with value of total and amount

```

{

total: 0,

amount: 0,

}

```

5. now when we return cartTotal then it is an object which have two value of cartTotal.total and cartTotal.amount.

6. cartItem is the each element of the array. first will go the first one then second one and so on.

7. we from the state.cart.reduce we will have an object and this object has two value total and amount. so we have already destructured it.

```

let { total, amount } = state.cart.reduce(function that return cartTotal,accumulator which is an object with value of total and amount)

```

as we can see it returns an object which has two value of total and amount.so we destructured it. 8. the total need to to parseFloat and toFixed(2) to get the value of two decimal point. 9. finally we return the state and total and amount.

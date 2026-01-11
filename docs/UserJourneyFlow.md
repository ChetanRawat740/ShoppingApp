# User Journey and Flow Diagrams

## Overview
This document outlines the user journey and flow diagrams for the e-commerce Android app, focusing on the shopping experience from app launch to purchase completion.

## Main User Journeys

### 1. Browse and Shop Journey

```
App Launch --> Home Screen --> Browse Categories --> View Items --> Add to Cart --> Checkout
     |             |                 |                   |              |            |
     |             |                 |                   |              |            |
     v             v                 v                   v              v            v
[Loading]    [Banner Display]  [Category Grid]    [Item Details]  [Cart Update]  [Order Complete]
```

### 2. Cart Management Journey

```
View Cart --> Modify Quantities --> Remove Items --> Apply Discounts --> Proceed to Checkout
     |              |                   |              |                   |
     |              |                   |              |                   |
     v              v                   v              v                   v
[Cart List]  [Quantity Controls]  [Delete Action]  [Promo Code]     [Payment Screen]
```

## Detailed Flow Diagrams

### App Launch Flow

```
User opens app
    |
    v
Check for stored data (TinyDB)
    |
    +---------------------+
    | Network available?  |
    +---------------------+
    |         |           |
    | No      | Yes       |
    v         v           v
Load cached  Fetch remote  Fetch remote data
data         data         (Firebase)
    |         |           |
    |         +-----------+
    v
Display home screen
    |
    v
Show banners and categories
```

### Category Browsing Flow

```
Home Screen
    |
    v
User selects category
    |
    v
Load category items
    |
    +---------------------+
    | Items available?    |
    +---------------------+
    |         |           |
    | No      | Yes       |
    v         v           v
Show empty   Display item  Display item grid
state        list         with images
    |         |           |
    |         +-----------+
    v
User can browse items
```

### Item Details Flow

```
Item selected from list/grid
    |
    v
Load item details
    |
    v
Display item information:
- Title
- Description
- Images (swipeable)
- Price
- Rating
- Size options
    |
    +---------------------+
    | User action         |
    +---------------------+
    |         |           |
    | Add to   | View     |
    | Cart     | Cart     |
    v         v           v
Update cart  Navigate to  Navigate to cart
(TinyDB)     cart screen   screen
```

### Cart Management Flow

```
Cart Screen
    |
    v
Display cart items
(ItemsModel list from TinyDB)
    |
    +---------------------+
    | Cart empty?         |
    +---------------------+
    |         |           |
    | Yes     | No        |
    v         v           v
Show empty   Show item    Show item list with:
cart msg     list         - Quantity controls
    |         |           - Remove buttons
    |         +-----------+ - Price calculations
    v
User can:
- Modify quantities
- Remove items
- Apply promo codes
- Proceed to checkout
```

### Checkout Flow

```
Cart Screen --> Checkout Button --> Payment Screen --> Order Confirmation
     |              |                   |                   |
     |              |                   |                   |
     v              v                   v                   v
[Validate Cart]  [Calculate Total]  [Payment Processing]  [Order Complete]
[Check Stock]    [Apply Discounts]  [Success/Failure]     [Update Cart]
```

## User Experience Considerations

### Key Touchpoints
1. **App Launch**: Fast loading, offline capability
2. **Browsing**: Smooth scrolling, image loading
3. **Item Details**: Clear information, easy size selection
4. **Cart Management**: Intuitive quantity controls
5. **Checkout**: Secure payment, order confirmation

### Error Handling Flows

```
Any screen --> Error occurs --> Display error message --> Retry option
     |              |                   |                   |
     |              |                   |                   |
     v              v                   v                   v
[Network Error]  [User-friendly]     [Retry Button]       [Return to flow]
[Data Error]     [messages]          [Cancel Option]      [or exit]
```

### Offline Scenarios

```
App offline --> Attempt action --> Check connectivity --> Show offline message
     |              |                   |                   |
     |              |                   |                   |
     v              v                   v                   v
[Cached Data]   [Network Check]     [Retry when online]  [Limited functionality]
[Local Cart]    [Fail gracefully]   [Save for later]     [Inform user]
```

## Performance Considerations

### Loading States
- Skeleton screens during data fetching
- Progressive image loading
- Cached data for faster subsequent loads

### Responsiveness
- Smooth transitions between screens
- Immediate feedback for user actions
- Optimized image sizes for different screen densities

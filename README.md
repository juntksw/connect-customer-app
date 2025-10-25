[Uploading README (1).md…]()
# CONNECT Customer Manager v3.5

## 🎯 New in v3.5: Quantity Selector & Tap-to-Enter Amount

### Overview
In v3.5, two major improvements have been added for handling multiple purchases:
1. **Quantity Selector**: +/- buttons to select 1-10 bowls per visit
2. **Tap-to-Enter Numpad**: Touch-friendly numpad for easy amount entry

Staff can now quickly process multiple bowl purchases with intuitive tap controls.

### Why This Feature?

**Real-World Scenario:**
- Customer purchases 3 acai bowls → Should receive 3 stamps
- Customer purchases 1 bowl with toppings → Total amount varies, but still 1 stamp
- Previously: Staff had to manually add stamps or create multiple visit records

**Solution:**
- ✅ Intuitive +/- buttons to select quantity
- ✅ Visual quantity display
- ✅ Automatic stamp calculation based on quantity
- ✅ Single visit record with quantity notation

---

## 📱 How to Use (v3.5)

### Recording Multiple Purchases

1. **Select Customer**
   - Search and select customer from list

2. **Click "Add Visit"**
   - Form opens with quantity selector

3. **Set Quantity**
   - Default: 1 bowl
   - Click **[+]** to increase (max: 10)
   - Click **[−]** to decrease (min: 1)
   - Number displays in the center

4. **Enter Details**
   - Menu Item: e.g., "Original Acai Bowl"
   - Total Amount: Tap numpad to enter total price
     - Tap numbers: [1] [5] [0] [0]
     - Result: $15.00
     - Use [⌫] to delete, [Clear] to reset
     - Use [・] for decimal point
     - Use [00] for quick entry

5. **Save Visit**
   - Click "Save Visit"
   - Stamps automatically added = Quantity selected
   - Menu recorded as "Original Acai Bowl x3" (if quantity > 1)

### Example Scenarios

**Scenario 1: Single Bowl Purchase**
```
Menu Item: Original Acai Bowl
Quantity: [−] [1] [+]  (default)
Total Amount: $5.00
Result: +1 stamp
History: "Original Acai Bowl - $5.00"
```

**Scenario 2: Multiple Bowls**
```
Menu Item: Original Acai Bowl
Quantity: [−] [3] [+]  (click + twice)
Total Amount: $15.00
Result: +3 stamps
History: "Original Acai Bowl x3 - $15.00"
```

**Scenario 3: Bowl with Premium Toppings**
```
Menu Item: Original Acai Bowl
Quantity: [−] [1] [+]
Total Amount: Tap [8] [・] [5] [0] → $8.50
Result: +1 stamp
History: "Original Acai Bowl - $8.50"
```

**Scenario 4: Quick Entry with [00]**
```
Menu Item: Original Acai Bowl
Quantity: [−] [2] [+]
Total Amount: Tap [1] [0] [00] → $10.00
Result: +2 stamps
History: "Original Acai Bowl x2 - $10.00"
```

---

## 🎨 UI Design

### 1. Quantity Selector

```
Quantity (Stamps to Add)
┌─────────────────────────────┐
│   [−]    [3]    [+]         │
│   btn   display  btn        │
└─────────────────────────────┘
```

**Features:**
- **[−] Button**: Purple bordered, decreases quantity
- **Display**: Purple gradient box with current number
- **[+] Button**: Purple bordered, increases quantity
- **Limits**: Min: 1, Max: 10 (buttons auto-disable)
- **Touch-Friendly**: 45px large tap targets

### 2. Tap-to-Enter Numpad

```
Total Amount
┌─────────────────────────────┐
│     $15.00                  │  ← Green gradient display
└─────────────────────────────┘

┌─────────────────────────────┐
│  [1]  [2]  [3]  [⌫]      │
│  [4]  [5]  [6]  [・]      │
│  [7]  [8]  [9]  [00]     │
│  [Clear]    [0]          │
└─────────────────────────────┘
```

**Features:**
- **Display**: Green gradient, large text ($XX.XX)
- **[1-9]**: White buttons with number input
- **[0]**: Single-width zero button
- **[00]**: Quick double-zero entry (yellow)
- **[・]**: Decimal point (yellow)
- **[⌫]**: Backspace/delete last digit (yellow)
- **[Clear]**: Reset to $0.00 (red, 2x width)
- **Max Amount**: $999.99
- **Touch-Friendly**: Large buttons with hover effects

---

## 🔄 Changes from v3.4

### New Features
- ✅ Quantity selector with +/- buttons (1-10)
- ✅ Visual quantity display with gradient
- ✅ **Tap-to-enter numpad** for amount input
- ✅ Large touch-friendly buttons (mobile optimized)
- ✅ Quick entry buttons ([00], [・], [⌫])
- ✅ Real-time amount display ($XX.XX)
- ✅ Multiple stamps per visit
- ✅ Quantity notation in history (e.g., "x3")
- ✅ Smart 10-stamp overflow handling

### Updated Logic
- **Visit Recording**: Now includes quantity
- **Stamp Addition**: Based on selected quantity
- **10-Stamp Overflow**: 
  - Example: 8 stamps + 3 new = 10 (reward) + 1 overflow
  - System prompts to reset and add overflow stamps

### CSS Additions
- `.quantity-selector` - Quantity container
- `.quantity-btn` - +/- buttons
- `.quantity-display` - Number display
- `.amount-display` - Amount display (green gradient)
- `.numpad` - 4-column grid layout
- `.numpad-btn` - Base button styles
- `.numpad-btn.special` - Yellow accent ([00], [・], [⌫])
- `.numpad-btn.clear` - Red clear button
- `.numpad-btn.zero` - Single-width zero
- Hover, active, and disabled states

### JavaScript Additions
- `currentQuantity` - Tracks selected quantity
- `currentAmount` - Tracks entered amount
- `changeQuantity(delta)` - Quantity +/- handler
- `updateQuantityDisplay()` - Updates quantity UI
- `numpadInput(value)` - Number/decimal input
- `numpadBackspace()` - Delete last digit
- `numpadClear()` - Reset to $0.00
- `updateAmountDisplay()` - Updates amount display
- Modified `showAddVisitForm()` - Resets both quantity and amount
- Modified `addVisit()` - Uses currentAmount, handles overflow

---

## 📊 Operation Flow (v3.5)

```
Customer purchases multiple bowls
    ↓
Click "Add Visit"
    ↓
Set quantity using +/- buttons
    ↓
Enter menu & total amount
    ↓
Click "Save Visit"
    ↓
Automatically:
  ✅ Visit recorded (with quantity notation)
  ✅ Stamps added = Quantity
  ✅ Total spent updated
  ✅ Handle 10-stamp limit & overflow
  ✅ Reward notification (if earned)
  ✅ Progress notification (otherwise)
```

---

## 🎉 Previous Features (Still Available)

### v3.4 Features
- Simplified UI (single "Add Visit" button)
- Guaranteed data consistency

### v3.3 Features
- Reward notification animations (English)
- Progress notifications with remaining stamps
- "Congratulations!" (golden) / "Almost There!" (purple)

### v3.2 Features
- Custom stamp icons (🥣🍓💰🍵🎁)
- Reward redemption tracking
- Redeemed rewards history

### Earlier Features
- Customer management (add/search/delete)
- Gender & age tracking
- Monthly TOP5 ranking
- Firebase real-time sync
- Multi-device support

---

## 🧪 Testing Checklist

### Quantity Selector
- [ ] Default quantity = 1
- [ ] [+] button increases quantity
- [ ] [−] button decreases quantity
- [ ] Cannot go below 1 (button disabled)
- [ ] Cannot go above 10 (button disabled)
- [ ] Display shows current quantity
- [ ] Buttons have hover effects

### Numpad Input
- [ ] Default amount = $0.00
- [ ] Number buttons input correctly
- [ ] [00] button adds double zero
- [ ] [・] button adds decimal point
- [ ] Cannot add multiple decimal points
- [ ] [⌫] deletes last digit
- [ ] [Clear] resets to $0.00
- [ ] Display shows $XX.XX format
- [ ] Max amount $999.99 enforced
- [ ] Touch-friendly button sizes

### Stamp Addition
- [ ] Quantity 1 → +1 stamp
- [ ] Quantity 3 → +3 stamps
- [ ] Quantity 5 → +5 stamps

### Visit History
- [ ] Quantity 1: "Menu Item"
- [ ] Quantity 3: "Menu Item x3"
- [ ] Total amount recorded correctly

### 10-Stamp Overflow
- [ ] 8 stamps + 2 = 10 (reward prompt)
- [ ] 8 stamps + 3 = 10 + 1 overflow (prompt to reset and add 1)
- [ ] 9 stamps + 5 = 10 + 4 overflow (prompt to reset and add 4)

### Reward Notifications
- [ ] Single stamp reaching 2/5/8/10 triggers notification
- [ ] Multiple stamps crossing thresholds trigger notification
- [ ] Animations display correctly

### Mobile Responsiveness
- [ ] Buttons are touch-friendly (45px)
- [ ] Layout works on small screens
- [ ] Text is readable

---

## 📦 File Information

- **index.html**: 70KB (1,997 lines)
- **manifest.json**: 684B
- **Version**: v3.5
- **Backup**: `/mnt/aidrive/CONNECT_Acai_App/connect_acai_app_v3.5.zip`

---

## 📚 Version History

### v3.5 (Current)
- Added quantity selector for multiple purchases
- Support for 1-10 bowls per visit
- Smart overflow handling for 10-stamp limit
- Quantity notation in visit history

### v3.4
- Removed "Add Stamp" button
- Simplified UI for guaranteed data consistency

### v3.3
- Reward notification animations
- Progress notifications
- All texts in English

### v3.2
- Custom stamp icons
- Reward redemption tracking
- Redeemed rewards history

### v3.1
- Customer deletion feature

### v3.0
- Gender & age information
- Total spent calculation
- Monthly TOP5 ranking

### v2.0
- Firebase Firestore integration
- Real-time multi-device sync

### v1.0
- Local storage version
- Basic stamp card system

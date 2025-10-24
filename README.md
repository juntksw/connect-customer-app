# CONNECT Customer Manager

Customer management application for CONNECT Acai & Cafe, Phnom Penh, Cambodia.

## Features

✅ **Customer Management**
- Add new customers with name and Telegram phone number
- Search customers by name
- View customer details and history

✅ **Digital Stamp Card System**
- Track customer stamps (max 10)
- Automatic reward display:
  - 2 stamps → FREE +1 topping
  - 5 stamps → 50% OFF
  - 8 stamps → FREE MATCHA
  - 10 stamps → Baby Size Acai Bowl FREE
- Auto-reset at 10 stamps

✅ **Visit History Tracking**
- Record visit date/time
- Track purchased menu items
- Track purchase amounts

✅ **Telegram Broadcast**
- Send bulk messages to all customers
- Integrated with Telegram Bot API

✅ **Data Backup**
- Manual backup (export JSON)
- Import backup to restore data
- Auto-backup option

## Installation

### Option 1: Host on Free Platform (Recommended)

1. **Using Netlify (Free)**:
   - Go to https://app.netlify.com/drop
   - Drag and drop the entire `connect_acai_app` folder
   - Get your app URL instantly!

2. **Using GitHub Pages (Free)**:
   - Create a GitHub account
   - Create a new repository
   - Upload all files
   - Enable GitHub Pages in settings
   - Access at: `https://yourusername.github.io/repo-name`

### Option 2: Local Testing

1. Open `index.html` in a web browser
2. All data is stored locally in the browser

## How to Use

### Adding New Customer
1. Go to "Add New" tab
2. Enter customer name
3. Enter Telegram phone number (format: +855 12 345 678)
4. Click "Add Customer"

### Recording a Visit
1. Click on customer name from list
2. Click "Add Visit" button
3. Enter menu item and amount
4. Click "Save Visit"
- This automatically adds 1 stamp

### Adding Just a Stamp
1. Click on customer name
2. Click "Add Stamp" button

### Sending Broadcast Message
1. Go to "Broadcast" tab
2. Type your message
3. Click "Send Broadcast"

**Important**: For Telegram broadcast to work, customers must:
1. Have started a chat with your bot first
2. Use the exact phone number registered with Telegram

### Telegram Bot Setup

Your bot is already created! Bot username: `@connect_acai_bot`

To allow customers to receive messages:
1. Share this link with customers: https://t.me/connect_acai_bot
2. Ask them to click "START" button
3. Now they can receive your broadcasts!

### Backing Up Data

**Manual Backup**:
1. Go to "Backup" tab
2. Click "Download Backup"
3. Save the JSON file to a safe location

**Restore Backup**:
1. Go to "Backup" tab
2. Click "Restore from Backup"
3. Select your backup JSON file

**Auto Backup**:
1. Go to "Backup" tab
2. Click "Enable Auto Backup"
3. Data will be backed up daily automatically

## Technical Details

- **Type**: Progressive Web App (PWA)
- **Storage**: Browser LocalStorage
- **Offline**: Works without internet (except Telegram broadcast)
- **Device**: Mobile-optimized (works on all devices)
- **Languages**: English interface (can be customized)

## Data Structure

```javascript
{
  id: timestamp,
  name: "Customer Name",
  phone: "+855 12 345 678",
  stamps: 0-10,
  joinedDate: "ISO date",
  visits: [
    {
      date: "ISO date",
      menu: "Menu item name",
      amount: 0.00
    }
  ]
}
```

## Telegram Bot Commands

Your bot token is embedded in the app (secure for single-user app).

To send messages programmatically:
```
POST https://api.telegram.org/bot8280988484:AAF35cs0TLiNIWACrV5zRy89OoUEVLf_xdM/sendMessage
{
  "chat_id": "phone_number",
  "text": "Your message"
}
```

## Troubleshooting

### Telegram messages not sending?
- Make sure customer has started chat with bot
- Check phone number format (+855 12 345 678)
- Verify internet connection

### Data disappeared?
- Check if using same browser/device
- Restore from backup
- Check if browser storage was cleared

### App not loading?
- Clear browser cache
- Try different browser
- Check internet connection (for first load)

## Support

For issues or questions about this app, contact the developer.

## License

Custom built for CONNECT Acai & Cafe. All rights reserved.

# HEXAVORA Contact Integration - Setup Guide

## 🚀 What's Been Added

### 1. Professional Contact Methods
Four clickable contact options have been added to the contact section:
- **Email**: hexavoratech@gmail.com → Opens mail app
- **Instagram**: @hexavora_dev → Opens Instagram profile
- **Phone**: +91 9930101243 → Initiates phone call
- **LinkedIn**: HEXAVORA → Opens LinkedIn profile

Each contact method features:
- Minimal futuristic icon-based card design
- Hover effects matching the site's aesthetic
- Smooth transitions and responsive layout
- Support for both light and dark (OS state) themes

### 2. Web3Forms Integration
Form submission now sends directly to Gmail via Web3Forms.

**How it works:**
- Form data is validated client-side
- Submits to: https://api.web3forms.com/submit
- Receives responses directly in Gmail
- All form data preserved in email

**Form fields submitted:**
- Name
- Email
- Budget range
- Project type
- Message

### 3. Enhanced Button States
The submit button now shows clear submission progress:

```
INITIATE INQUIRY  ← Default state
     ↓ (on click)
TRANSMITTING...   ← Loading state (with spinner)
     ↓ (on success)
INQUIRY SENT      ← Success state (2.2 seconds)
     ↓ (after delay)
INITIATE INQUIRY  ← Returns to default
```

### 4. Form Features
✅ Full client-side validation
✅ Real-time error messages
✅ Success notification
✅ Automatic form reset
✅ Graceful error handling
✅ Loading indicator
✅ Responsive on all devices

---

## ⚙️ Setup Instructions

### Step 1: Get Web3Forms Access Key
1. Go to https://web3forms.com
2. Sign up with your Gmail account
3. Copy your Access Key
4. In `index.html`, find this line (around line 1717):
```html
<input type="hidden" name="access_key" value="e1477cbd-fa5a-4ff1-aa56-ec2e8c22a8dd">
```
5. Replace `YOUR_ACCESS_KEY_HERE` with your actual access key

### Step 2: Verify Contact Details
Contact information is hardcoded at lines 1695-1720:
- **Email**: hexavoratech@gmail.com
- **Instagram**: https://www.instagram.com/hexavora_dev?igsh=a3dhcWJyaDMweGZ0
- **Phone**: +91 9930101243

Update these values as needed by editing the onclick handlers and text content.

### Step 3: Test the Form
1. Open the website
2. Scroll to Contact section
3. Try clicking each contact method
4. Fill out the form and submit
5. Check your Gmail for the inquiry submission

---

## 🎨 Design Notes

### Styling Consistency
- All new elements use existing design tokens (colors, spacing, fonts)
- Contact methods cards inherit `.card` styling
- Hover states match existing patterns
- Animations aligned with GSAP framework

### Color Variables Used
- `--accent`: Primary color for icons (#6b5cf6)
- `--accent-soft`: Soft background for icons (rgba(107,92,246,0.12))
- `--border`: Card borders (uses CSS vars for theme)
- `--text-primary` / `--text-secondary`: Text colors

### Responsive Breakpoints
- Mobile (< 768px): Stacked contact methods, full-width form
- Tablet (768px - 1279px): 2-column grid for methods
- Desktop (> 1279px): 1-column contact methods, side-by-side form

---

## 🔧 Customization

### Changing Contact Methods
Edit the `<ul class="contact-methods">` section (~line 1695-1720):

```html
<li class="contact-method" onclick="window.location.href='mailto:hexavoratech@gmail.com'; return false;">
  <div class="contact-method-icon">✉</div>
  <div class="contact-method-content">
    <span class="contact-method-label">Email</span>
    <span class="contact-method-value">YOUR_EMAIL</span>
  </div>
</li>
```

### Changing Button Text
The button text supports both agency and OS modes (lines 1724-1727):
- Agency mode: "Send Inquiry"
- OS mode: "INITIATE INQUIRY"

### Form Submission Email
Customize the email subject line in this hidden input (~line 1717):
```html
<input type="hidden" name="subject" value="New Project Inquiry from HEXAVORA Website">
```

---

## 📝 Key Files & Locations

### CSS Additions
- Lines 561-632: Contact methods styling
- Lines 202-232: Button loading states
- Lines 565-580: Dark theme support

### HTML Updates
- Lines 1693-1720: Contact methods list
- Lines 1716-1727: Form with Web3Forms integration
- Lines 1724-1727: Submit button with state markup

### JavaScript Updates
- Lines 1904-1975: Enhanced initForm() function
- Web3Forms API integration
- Button state management
- Error handling

---

## ❓ Troubleshooting

### Form not submitting?
1. Check if access_key is set correctly
2. Verify internet connection
3. Check browser console for errors (F12)
4. Ensure all form fields are filled

### Contact links not working?
1. Verify email addresses and URLs
2. Check mailto/tel protocol support
3. Try in incognito mode to rule out extensions

### Styling looks off?
1. Clear browser cache (Ctrl+Shift+Delete)
2. Hard refresh page (Ctrl+F5)
3. Check if dark mode (OS state) is activating
4. Verify CSS variables are applied

---

## 📧 Support

For Web3Forms support: https://web3forms.com/help
For HTML/CSS/JS questions: Check inline comments in index.html

---

**Last Updated:** May 28, 2026
**Status:** Production Ready

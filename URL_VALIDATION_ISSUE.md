# Security Issue: Missing URL Validation on Link Creation

## 🚨 Severity: High

## 📋 Issue Description

The Conn platform currently does not validate URLs when users create or update links through the admin dashboard. This poses a security risk and can lead to poor user experience.

## 🔍 Current Behavior

In `server.js`, the link creation and update endpoints directly accept user-provided URLs without validation:

### POST /api/links (Line 452)
```javascript
url: req.body.url || 'https://',
```

### PUT /api/links/:id (Line 489)
```javascript
if (req.body.url !== undefined) updates.url = req.body.url;
```

## ⚠️ Security & User Experience Risks

1. **Malicious URLs**: Users can submit potentially harmful URLs (javascript:, data:, file: protocols)
2. **Invalid Formats**: Non-URL strings can be saved, causing broken links
3. **XSS Potential**: Malicious URLs could be executed when clicked
4. **Poor UX**: Users may accidentally save invalid URLs without knowing
5. **Data Integrity**: Database contains potentially malformed data

## 🎯 Proposed Solution

Add comprehensive URL validation for both creation and update endpoints:

### 1. URL Validation Function
```javascript
function isValidUrl(url) {
  if (!url || typeof url !== 'string') return false;
  
  // Basic URL format validation
  const urlRegex = /^https?:\/\/(www\.)?[-a-zA-Z0-9@:%._\+~#=]{1,256}\.[a-zA-Z0-9()]{1,6}\b([-a-zA-Z0-9()@:%_\+.~#?&//=]*)$/;
  
  if (!urlRegex.test(url)) return false;
  
  // Block dangerous protocols
  const dangerousProtocols = ['javascript:', 'data:', 'file:', 'ftp:', 'blob:'];
  const protocol = url.toLowerCase().split(':')[0] + ':';
  
  if (dangerousProtocols.includes(protocol)) return false;
  
  return true;
}
```

### 2. Validation in Endpoints
- Add validation in POST `/api/links` before database insertion
- Add validation in PUT `/api/links/:id` before database update
- Return appropriate error messages for invalid URLs

### 3. Client-Side Validation
- Add URL validation in `public/js/admin.js` for immediate feedback
- Show helpful error messages to users

## 📝 Acceptance Criteria

- [ ] Server validates URL format before saving to database
- [ ] Dangerous protocols (javascript:, data:, etc.) are blocked
- [ ] Clear error messages returned for invalid URLs
- [ ] Client-side validation provides immediate feedback
- [ ] Existing invalid URLs in database are handled gracefully
- [ ] Unit tests added for URL validation function

## 🧪 Test Cases

Valid URLs to allow:
- `https://example.com`
- `http://www.example.com`
- `https://subdomain.example.com/path?query=value`
- `https://example.com:8080/path`

Invalid URLs to block:
- `javascript:alert('xss')`
- `data:text/html,<script>alert('xss')</script>`
- `file:///etc/passwd`
- `not-a-url`
- `ftp://example.com`
- Empty string or null values

## 🔧 Implementation Steps

1. Create URL validation helper function in `server.js`
2. Add validation to POST `/api/links` endpoint
3. Add validation to PUT `/api/links/:id` endpoint
4. Add client-side validation in `admin.js`
5. Add appropriate error handling and user feedback
6. Add unit tests
7. Update API documentation

## 🎯 Impact

- **Security**: Prevents XSS and malicious URL attacks
- **User Experience**: Better feedback and error handling
- **Data Quality**: Ensures only valid URLs are stored
- **Maintainability**: Centralized validation logic

## 🏷️ Labels

`security`, `bug`, `high-priority`, `validation`, `backend`, `frontend`

## 🔗 Related Issues

- Could be part of a larger input validation initiative
- Related to #2 (Generic Error Messages) - this would provide specific error messages

## 📊 Additional Notes

This is a high-priority security issue that should be addressed promptly. The fix is straightforward but critical for maintaining the security and integrity of the platform.

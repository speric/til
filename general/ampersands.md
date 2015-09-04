Having an ampersand in an email address may/may not pass certain validations, but it will be escaped if sent as the value of an XML request (say, to a payment gateway endpoint). This is because of [http://www.w3.org/TR/REC-xml/#dt-chardata](http://www.w3.org/TR/REC-xml/#dt-chardata):

>The ampersand character (&) and the left angle bracket (<) must not appear in their literal form, except when used as markup delimiters, or within a comment, a processing instruction, or a CDATA section. If they are needed elsewhere, they must be escaped using either numeric character references or the strings `&amp;` and `&lt;` respectively.

So `jane&doe@example.com` should become:

```
<Email>jane&amp;doe@example.com</Email>
```

If you're sending XML, expect that to be the case. If you're receiving XML, you should also expect that to be the case.

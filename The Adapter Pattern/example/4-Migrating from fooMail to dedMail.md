```javascript
/* existing code */
fooMail.getMail(function(text) {
    $('message-pane').innerHTML = text;
});
  
/* make an adapter with dedMail */  
var dedMailtoFooMailAdapter = {};
dedMailtoFooMailAdapter.getMail = function(id, callback) {
  dedMail.getMail(id, function(resp) {
  var resp = eval('('+resp+')');
  var details = '<p><strong>From:</strong> {from}<br>';
  details += '<strong>Sent:</strong> {date}</p>';
  details += '<p><strong>Message:</strong><br>';
  details += '{message}</p>';
  callback(DED.util.substitute(details, resp));
  });
};
// Other methods needed to adapt dedMail to the fooMail interface....
// Assign the adapter to the fooMail variable.
fooMail = dedMailtoFooMailAdapter;
```


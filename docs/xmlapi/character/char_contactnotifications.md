# ContactNotifications
Lists the notifications received about having been added to someone's contact list.

* __Path:__ ``/char/ContactNotifications.xml.aspx``
* __Cache timer:__ 30 minutes
* __Access mask:__ 32
* __Parameters:__
    <table border="1">
        <tbody>
            <tr>
                <th>Argument</th>
                <th>Type</th>
                <th>Description</th>
            </tr>
            <tr>
                <td>characterID</td>
                <td><strong>long</strong></td>
                <td>ID of character</td>
            </tr>
        </tbody>
    </table>

### Sample Response

```xml
<result>
    <rowset name="contactNotifications" key="notificationID" columns="notificationID,senderID,senderName,sentDate,messageData">
        <row notificationID="308734131" senderID="797400947" senderName="CCP Garthagk" sentDate="2010-05-29 23:04:00" messageData="level: 10&#xA;message: Hi, I want to social network with you!&#xA;" />
    </rowset>
</result>
```  

### Result Data

<table border="1">
    <tbody>
        <tr>
            <th>Name</th>
            <th>Data type</th>
            <th>Description</th>
        </tr>
        <tr>
            <td>notificationID</td>
            <td>long</td>
            <td>ID number of the notification.</td>
        </tr>
        <tr>
            <td>senderID</td>
            <td>long</td>
            <td>ID of character/agent/corp who initiated this notification message.</td>
        </tr>
        <tr>
            <td>senderName</td>
            <td>char</td>
            <td>Name of character/agent/corp who initiated this notification message.</td>
        </tr>
        <tr>
            <td>sentDate</td>
            <td>datetime</td>
            <td>Date/time notification was sent.</td>
        </tr>
        <tr>
            <td>messageData</td>
            <td>string</td>
            <td>Contents of the message (see notes).</td>
        </tr>
        <tr>
            <th colspan='3'>messageData contents</th>
        </tr>
        <tr>
            <td>level</td>
            <td>decimal</td>
            <td>The new standing.</td>
        </tr>
        <tr>
            <td>message</td>
            <td>string</td>
            <td>Actual message text.</td>
        </tr>
    </tbody>
</table>

### Notes

* messageData layout
    Message data is a string of name/value pairs, each pair terminated by a LF _(&amp;#xA;)_:    
    ```
    {name1}: {value1}
    {name2}: {value2}
    {name3}: {value3}
    ```

### References

[Tyrannis API Improvements](http://community.eveonline.com/news/dev-blogs/tyrannis-api-improvements/)

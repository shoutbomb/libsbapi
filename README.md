# libsbapi

Custom API for integration of Shoutbomb with Symphony. 

NOTES

customInformation fails on test, LOSFORMAT policy does not exist


SBAPI Validation

These are the SBAPI endpoints

URL: https://server:port/cgi-bin/sb.cgi?report=userkey&uid=21168045392313

Input: uid = patron barcode number

Output:


21168045392313
445800
NPO
99990101


URL: https://server:port/cgi-bin/sb.cgi?report=userbarcode&ukey=445800

Input: ukey = user internal key

Output:


21168045392313
445800
NPO
99990101


URL: https://server:port/cgi-bin/sb.cgi?report=hold&uid=21967002133994

Input: uid = patron barcode number

Output:

21967002133994


31967011537878
The violets of March : a novel / Sarah Jio
20110621
JBBB
20110626
< HOLD_DB_KEY>1234566


31967012061787
The search / Nora Roberts
20110620
JBBB
20110625
1234567




Portrait of a lady on fire


We summon the darkness



is needed to enable the cancellation of this item hold.

https://server:port/cgi-bin/sb.cgi?report=courtesy&uid=21967002133994

Input: uid = patron barcode number

Output:

21967002133994


31967010702333
Snacktime! / Barenaked Ladies
20110624



31967011418475
But not the hippopotamus / by Sandra Boynton
20110624



31967011418236
The going to bed book / by Sandra Boynton
20110624



31967011418350
Blue hat, green hat / Sandra Boynton
20110624




has the following possible values
11 - Item is not eligible for renewal due to outstanding fees
12 - Patron Status is BLOCKED or BARRED
13 - Item is on-hold
14 - Maximum number renewals for the item has been reached

https://server:port/cgi-bin/sb.cgi?report=overdue&uid=21967002133994

Input: uid = patron barcode number

Output:

21967002133994


31967011342030
End of days / Steve Alten
20110620
13


31967011066951
Sworn to silence / Linda Castillo
20110620
13



has the following possible values
11 - Item is not eligible for renewal due to outstanding fees
12 - Patron Status is BLOCKED or BARRED
13 - Item is on-hold
14 - Maximum number renewals for the item has been reached
15 - Item is not eligible for renewal due to limit set on how many overdue items a patron can have at one time

https://server:port/cgi-bin/sb.cgi?report=chkcharge&uid=21967002133994&id=31967011342030

Input: uid = patron barcode number
id = item barcode number

Output:

31967011342030
21967002133994
0

has the following possible values
0 - Item is not charged to patron
1 - Item is charged to patron

https://server:port/cgi-bin/sb.cgi?report=chkhold&id=31967011342030

Input: id = item barcode number

Output:

31967011342030
0

< ONHOLD> has the following possible values
0 - Item has no hold
1 - Item has a hold

https://server:port/cgi-bin/sb.cgi?report=fee&uid=21967002133994

Input: uid = patron barcode number

Output:

21967002133994

30.25


https://server:port/cgi-bin/sb.cgi?report=noticetype&type=sms

Input: type = sms or voice

Output:


21168045392313
5552221568</USER_ PHONENUMBER >


21168045392314
5552221578</USER_ PHONENUMBER >


https://server:port/cgi-bin/sb.cgi?report=cancel&uid=21967002133994&dbkey=1234566

Input: uid = patron barcode number
dbkey = hold DB key

Output:
< ITEM>
0</ HOLD_CANCEL_STATUS>
</ ITEM>

< HOLD_CANCEL_STATUS > has the following possible values
0 – Cancel item hold failed
1 – Cancel item hold succeeded

https://server:port/cgi-bin/sb.cgi?report=holdexpiration&date=20200817

Input: date = date item hold request expired, YYYYMMDD

Output:

< ITEM_INFO>
21168045392313
< ITEM_TITLE>Invisible Man
</ ITEM_INFO>
< ITEM_INFO>
21168045392333
< ITEM_TITLE>Invisible Woman
</ ITEM_INFO>

ShowMeKey
Validating the response to request for the internal ID when we provide the library card

GET
userkey
https://lib-api-dev.multcolib.org:58461/cgi-bin/sb.cgi?report=userkey&uid=21168045918653
userkey returns user key and other patron related information when querying with a library card number

Request Params
report
userkey
report ID

uid
21168045918653
GET
userkey fail
https://lib-api-dev.multcolib.org:58461/cgi-bin/sb.cgi?report=userkey&uid=999
userkey returns user key and other patron related information when querying with a library card number

Request Params
report
userkey
report ID

uid
999
Library card

ShowMeBarcode
Validating the response to request for the patron library card when we provide the internal ID

GET
userbarcode
https://lib-api-dev.multcolib.org:58461/cgi-bin/sb.cgi?report=userbarcode&ukey=593963
userkey returns user key and other patron related information when querying with a library card number

Request Params
report
userbarcode
report ID

ukey
593963
GET
userbarcode fail
https://lib-api-dev.multcolib.org:58461/cgi-bin/sb.cgi?report=userkey&uid=999
userkey returns user key and other patron related information when querying with a library card number

Request Params
report
userkey
report ID

uid
999
Library card

ShowMeholds
Validating the response to request for the patron hold items when we provide the library card

GET
patronholds
https://lib-api-dev.multcolib.org:58461/cgi-bin/sb.cgi?report=hold&uid=21168045918653
userkey returns user key and other patron related information when querying with a library card number

Request Params
report
hold
report ID

uid
21168045918653
Library card

GET
patronholds fail
https://lib-api-dev.multcolib.org:58461/cgi-bin/sb.cgi?report=hold&uid=999
userkey returns user key and other patron related information when querying with a library card number

Request Params
report
hold
uid
999
ShowMecourtesy
Validating the response to request for the patron courtesy items due soon when we provide the library card

GET
patroncourtesy
https://lib-api-dev.multcolib.org:58461/cgi-bin/sb.cgi?report=courtesy&uid=21168045918653
userkey returns user key and other patron related information when querying with a library card number

Request Params
report
courtesy
report ID

uid
21168045918653
Library card

GET
patroncourtesy fail
https://lib-api-dev.multcolib.org:58461/cgi-bin/sb.cgi?report=hold&uid=999
userkey returns user key and other patron related information when querying with a library card number

Request Params
report
hold
uid
999
ShowMeoverdue
Validating the response to request for the patron overdue items when we provide the library card

GET
patronoverdue
https://lib-api-dev.multcolib.org:58461/cgi-bin/sb.cgi?report=overdue&uid=21168045918653
userkey returns user key and other patron related information when querying with a library card number

Request Params
report
overdue
report ID

uid
21168045918653
Library card

GET
patronoverdue fail
https://lib-api-dev.multcolib.org:58461/cgi-bin/sb.cgi?report=overdue&uid=999
userkey returns user key and other patron related information when querying with a library card number

Request Params
report
overdue
uid
999
ShowMeChargedItem
Validating the response to request for the patron overdue items when we provide the library card

GET
patronchargeditem
https://lib-api-dev.multcolib.org:58461/cgi-bin/sb.cgi?report=chkcharge&uid=21168045918653&id=31168131137091
userkey returns user key and other patron related information when querying with a library card number

Request Params
report
chkcharge
report ID

uid
21168045918653
Library card

id
31168131137091
item barcode

GET
patronchargeditem fail
https://lib-api-dev.multcolib.org:58461/cgi-bin/sb.cgi?report=chkcharge&uid=999&id=31168131137091
userkey returns user key and other patron related information when querying with a library card number

Request Params
report
chkcharge
uid
999
id
31168131137091
GET
patronchargeditem fail 2
https://lib-api-dev.multcolib.org:58461/cgi-bin/sb.cgi?report=chkcharge&uid=21168045918653&id=999
userkey returns user key and other patron related information when querying with a library card number

Request Params
report
chkcharge
uid
21168045918653
id
999
ShowMeOnHold
Validating the response to request for the patron overdue items when we provide the library card

GET
itemhashold
https://lib-api-dev.multcolib.org:58461/cgi-bin/sb.cgi?report=chkhold&id=31168131137091
userkey returns user key and other patron related information when querying with a library card number

Request Params
report
chkhold
report ID

id
31168131137091
GET
itemhashold fail
https://lib-api-dev.multcolib.org:58461/cgi-bin/sb.cgi?report=chkhold&id=999
userkey returns user key and other patron related information when querying with a library card number

Request Params
report
chkhold
id
999
ShowMeFees
Validating the response to request for the patron overdue items when we provide the library card

GET
feeinfo
https://lib-api-dev.multcolib.org:58461/cgi-bin/sb.cgi?report=fee&uid=21168045918653
userkey returns user key and other patron related information when querying with a library card number

Request Params
report
fee
report ID

uid
21168045918653
GET
feeinfo fail
https://lib-api-dev.multcolib.org:58461/cgi-bin/sb.cgi?report=fee&uid=999
userkey returns user key and other patron related information when querying with a library card number

Request Params
report
fee
uid
999

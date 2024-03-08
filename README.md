# Surfguard

## Introduction
Drive-by downloads are used to describe malicious programs that are downloaded to a user's computer when the users visit a website. Some downloads take advantage of unpatched computers, exploiting known vulnerabilities in the browser and operating system to install software silently in the background, without the user's knowledge. Other downloads are performed by tricking the user into downloading the software, by appearing to be the download of an essential plugin or other seemingly legitimate software. Drive-by downloads are particularly dangerous because of their stealthy nature i.e. they automatically install software on end users' computers without them knowing. The real severity of this particular type of attack is that it is entirely silent. Generally, website owners have no idea that this attack has occurred and that their website is leading to serious compromise of their own customers' security.

The approaches developed to combat these attacks are categorized into Signature based and Behavior based systems. With Signature analysis, the webpages are matched against databases containing exploit signatures; if virus is not yet added to the database, it bypasses the protection mechanism. Behavioral analysis on the other hand is very effective against zero-day attacks as they rely on detecting deviations in normal behavior of a process like monitoring system processes, kernel level hooks, monitoring file system changes etc. 
SurfGuard is a defense mechanism which relies on behavioral analysis of webpages at the Browser level. This relies on the fact that the actual decision of if a page is malicious or not comes into picture when the page is downloaded and being interpreted by the browser, hence making the browser the perfect point to place the defense mechanism. 
SurfGuard phases

SurfGuard’s protection mechanism relies on hooking the native Javascript APIs that are frequently used in the exploits. Based on the collected details from the exploits, some preliminary checking and filtering of the data is done in the hooked processes.
SurfGuard is developed as an exclusive JavaScript tool. The universal language allows the tool to be platform compatible and easily migrated across browsers. The current prototype works on Mozilla Firefox and Google Chrome browser.  It can easily detect and mitigate heap spray exploits, malicious redirections, attacks from iframes, suspicious links on page etc. The following snapshots shows the advantages of SurfGuard being used in the browser.
Webpage with link to malicious site






		Ordinary browser 				     SurfGuard enabled browser
The webpage shown above contains links to malicious sites on links ‘Games & gear’ and ‘Internet access’. Clicking on any of the links leads to some malware distribution site. With SurfGuard enabled browser, both the links are disabled to prevent user from clicking the links in the first place.
Webpage with malicious Iframe







Webpage with malicious iFrame viewed with Ordinary browser
When this webpage is opened in an ordinary browser, it successfully creates an inline Frame on the page which actually hosts a blacklisted site as shown in figure above. The same page with SurfGuard enabled browser, raises an alert for attempt to creation of malicious iFrame and also suppresses the creation by nuling out the source url resulting in creation of empty inline frame as shown below. The rest of the HTML page code remains undisturbed.







Webpage with malicious iFrame viewed with SurfGuard enabled browser


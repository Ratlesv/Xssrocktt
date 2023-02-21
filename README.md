# BHEH's XSSRocket

<p align="center">
<a href="https://www.blackhatethicalhacking.com"><img src="https://pbs.twimg.com/profile_banners/770898848197795840/1650879597/1500x500" width="600px" alt="BHEH"></a>
</p>
<p align="center">
<a href="https://www.blackhatethicalhacking.com"><img src="https://www.blackhatethicalhacking.com/wp-content/uploads/2022/06/BHEH_logo.png" width="300px" alt="BHEH"></a>
</p>

<p align="center">
XSS Rocket is written by Black Hat Ethical Hacking with the help of #ChatGPT as an experimentation, with a lot of hours spent modifying the code generated by ChatGPT and is designed for Offensive Security and XSS (Cross-Site scripting) attacks. 

Shout out and thanks to <a href="https://github.com/shadowdevnotreal"> ShadowDevnotreal

</p>

# Description

XSS Rocket, uses the **Wayback Machine** to fetch URLs and filters them based on parameters contained in the URLs. It then filters the URLs with **httpx** while using multiple **Grep** and **SED** patterns to filter only the ones that are alive and valid, removing the contents of the parameters and then uses a **remote XSS payload list from Github** to send **GET requests** with the payloads to the filtered URLs **injecting them with the XSS Payloads**, showcasing the status for **200 and 4XX errors** in Red and Green, and creating a **Summary for the findings**, while **saving all the results** into a folder that has the same name as the domain name created with all the results, inside it.

It also includes a **feature** that generates a random **Sun Tzu quote for Offensive Security** and uses lolcat to display colorful outputs and ASCII art and a check system to ensure that the user is connected to the internet before running it. 

What is special about this tool is that technically, is the **methodology** used and **critical thinking** behind it for each step that it is doing its action, but also by changing the payload wordlist, you could do more injection based attacks. This means you can modify it, so it can check for SQL Injections, OS Command Injection and so on! - **If you do change it, send us a push notification so we can add it!** You also get to perform stealth scans by changing the IP before each attack to evade various mechanisms. 

# Features:

• Supports Stealth Mode using Proxychains, for more reliable attacks against defensive mechanisms

• Automatically fetches URLs from the Wayback Machine

• Filters URLs based on parameters contained in the URLs

• Used httpx to filter only alive URLs and clearing the values for each parameter

• Uses a remote XSS payload list from Github

• Installs all requirements needed depending on the architecture as it gets new updates (Compatible with MacOS, Ubuntu, Debian, Kali)

• Sends GET requests with payload list to URLs

• Detects and reports possible XSS vulnerabilities

• Creates a folder with the domain name to save results

• Prints final message with number of possible vulnerable URLs and a Summary

• Saves result URLs in a file

• Display a random Sun Tzu quote for offensive security

• Check if the user is connected to the internet before running the tool

• Provides a way to append payloads to the URLs

• Output the full URL with payload

**This tool with also display a summary feature that displays the total number of possible XSS injections found, along with a list of affected URLs, the payload used, and the response code, at the end.**
    
It will, help you get the bounty of the bug while hunting:
    
![giphy-3](https://user-images.githubusercontent.com/13942386/220473071-db3d1fa8-bec7-47ce-9b46-9a8a8ed123e9.gif)


# Requirements:

• waybackurls: This tool can be installed by running go install github.com/tomnomnom/waybackurls@latest

• cURL: This tool is commonly pre-installed on Kali Linux and Ubuntu, but can be installed by running apt-get install curl on Ubuntu or brew install curl on MacOS

• figlet: This tool can be installed by running apt-get install figlet on Kali Linux or Ubuntu or brew install figlet on MacOS

• lolcat: This tool can be installed by running gem install lolcat

• wget: This tool is commonly pre-installed on Kali Linux and Ubuntu, but can be installed by running apt-get install wget on Ubuntu or brew install wget on MacOS

# Installation

`git clone https://github.com/blackhatethicalhacking/XSSRocket.git`

`cd XSSRocket`

`chmod +x XSSRocket.sh`

`./XSSRocket.sh`

# Screenshot

**Main Menu**


![Main](https://user-images.githubusercontent.com/13942386/214919576-c306a78f-419d-4110-8759-726ae188754c.png)



# Compatibility: 

This tool has been tested on Kali Linux, Ubuntu and MacOS.

# Payload Wordlist:

To change the list of payloads, you can edit the tool and set another URL.

# TO DO:

Ask the user towards the end, to email the results of the summary.

This is something that we will be using:

```
# Check if there were any affected URLs
if [ -s affected_urls.txt ]; then
    echo "A total of $counter possible XSS injections found."
    echo "Possible vulnerable URLs:"
    cat affected_urls.txt

    # Ask user if they want to email the results
    read -p "Do you want to email the results? (y/n): " email_results
    if [ "$email_results" == "y" ]; then
        # Set variables for the email
        recipient="example@email.com"
        subject="Vulnerability Results from BHEH_FAST_XSS_GPT for $domain"
        body="A total of $counter possible XSS injections found.\nPossible vulnerable URLs:\n$(cat affected_urls.txt)"
        summary="$(echo -e "$body")"
        smtp_url="smtp.mailtrap.io"
        smtp_port="2525"
        api_key="YOUR_API_KEY"

        # Send the email with curl
        curl --request POST \
             --url "smtp://$smtp_url:$smtp_port" \
             --data-urlencode "from=BHEH_FAST_XSS_GPT <from@email.com>" \
             --data-urlencode "to=$recipient" \
             --data-urlencode "subject=$subject" \
             --data-urlencode "text=$summary" \
             --user "$api_key:"
        echo -e "\nEmail sent!"
    fi
else
    echo "No vulnerabilities found."
fi
```

# Disclaimer

This tool is provided for educational and research purpose only. The author of this project are no way responsible for any misuse of this tool. 
We use it to test under NDA agreements with clients and their consents for pentesting purposes and we never encourage to misuse or take responsibility for any damage caused !

# Support

If you would like to support us, you can always buy us coffee(s)! :blush:

<a href="https://www.buymeacoffee.com/bheh" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/default-orange.png" alt="Buy Me A Coffee" height="41" width="174"></a>

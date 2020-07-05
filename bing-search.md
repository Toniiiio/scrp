Setup ist schwierig / nervig.

# Which service to use?

https://stackoverflow.com/questions/4082966/what-are-the-alternatives-now-that-the-google-web-search-api-has-been-deprecated
--> Bing.

# Reproducible code:

https://docs.microsoft.com/de-de/azure/cognitive-services/bing-web-search/quickstarts/client-libraries?pivots=programming-language-python

1. Install Python 3.x
2. Start cmd
3. Execute code:

Code in cmd:

    "C:\Users\User11\AppData\Local\Programs\Python\Python38\python.exe" -m venv mytestenv
    mytestenv\Scripts\activate.bat
    cd mytestenv
    "C:\Users\User11\AppData\Local\Programs\Python\Python38\python.exe" -m pip install azure-cognitiveservices-search-websearch
    
    
Create new file:

- within the newly created folder mytestenv with name, e.g. call.py --> C:\Users\User11\mytestenv\call.py
- modify code here: https://docs.microsoft.com/de-de/azure/cognitive-services/bing-web-search/quickstarts/client-libraries?pivots=programming-language-python

endpoint="https://api.cognitive.microsoft.com"

Key will come via mail. Not 100% sure how i initialized it, since i tried a lot of versions. Probably try cognitive service of azure as suggested by stackoverflow question: https://azure.microsoft.com/en-us/services/cognitive-services/bing-web-search-api/ and 
then select "7 day trial".
key you should receive in an email with subject "[Ihre API-Schlüssel] Willkommen bei Azure Cognitive Services"
Then there is a page with text like 
"Bing-Suche-APIs v7
Dieser API-Schlüssel ist zurzeit aktiv.
7 Tage verbleibend"
and at the bottom there are two keys. I tried the first one at it worked









Code

    # Import required modules.
    from azure.cognitiveservices.search.websearch import WebSearchClient
    from azure.cognitiveservices.search.websearch.models import SafeSearch
    from msrest.authentication import CognitiveServicesCredentials
    
    # Replace with your subscription key.
    subscription_key = "XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXx
    
    "
    
    # Instantiate the client and replace with your endpoint.
    client = WebSearchClient(endpoint="https://api.cognitive.microsoft.com", credentials=CognitiveServicesCredentials(subscription_key))
    
    # Make a request. Replace Yosemite if you'd like.
    web_data = client.web.search(query="Union Investment jobs")
    print("\r\nSearched for Query# \" Yosemite \"")
    
    '''
    Web pages
    If the search response contains web pages, the first result's name and url
    are printed.
    '''
    if hasattr(web_data.web_pages, 'value'):
    
        print("\r\nWebpage Results#{}".format(len(web_data.web_pages.value)))
        n_entries = len(web_data.web_pages.value)
        for entry in web_data.web_pages.value:
            print(entry.url)
    
        first_web_page = web_data.web_pages.value[0]
        print("First web page name: {} ".format(first_web_page.name))
        print("First web page URL: {} ".format(first_web_page.url))
    
    else:
        print("Didn't find any web pages...")



  

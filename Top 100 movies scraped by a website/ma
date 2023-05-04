from bs4 import BeautifulSoup
import requests
import os

URL = os.environ["url"]
# with open("website.html", encoding="utf8") as file:
#     contents = file.read()
#
# soup = BeautifulSoup(contents, "html.parser")
# print(soup.title.string)


response = requests.get(url="https://news.ycombinator.com/")
yc_webpage = response.text

soup = BeautifulSoup(yc_webpage, "html.parser")

artical_tag = soup.find_all(name="span", class_="titleline")
# print(artical_tag)
article_texts = []
article_links = []
for span in artical_tag:
    article_text = span.a.getText()
    article_texts.append(article_text)
    article_link = span.a.get("href")
    article_links.append(article_link)

# print(article_texts)
# print(article_links)
article_upvotes = [int(score.getText().split()[0]) for score in soup.find_all(name="span", class_="score")]
print(article_upvotes)
# print(len(article_upvotes))

highest_vote = 0
index = 0
for vote in article_upvotes:
    if highest_vote<vote:
        highest_vote = vote


# print(highest_vote)
index_of_highest_vote = article_upvotes.index(highest_vote)

highest_upvoted_text = article_texts[index_of_highest_vote]
highest_upvoted_link =  article_links[index_of_highest_vote]
print(highest_upvoted_text)
print(highest_upvoted_link)
print(index_of_highest_vote)

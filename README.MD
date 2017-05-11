{
 "cells": [
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "### Python Practices"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Below are the practices I did with Python. I hope someone will find them helpful someday. "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "#### 1. Simple Math and Print"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Note: Python will not print decimals if none of the numbers is an integer.  "
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {
    "collapsed": false
   },
   "outputs": [],
   "source": [
    "a = 2\n",
    "b = 3.\n",
    "c = b/a\n",
    "print(c)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "#### 2. String: Split and Joint, Count"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {
    "collapsed": false
   },
   "outputs": [],
   "source": [
    "text = \"The quick brown fox jumped over the lazy log.\"\n",
    "mytext = text.split()\n",
    "print(mytext)\n",
    "print(\" \".join(mytext))\n",
    "print(text.find(\"fox\"))\n",
    "\n",
    "count = 0\n",
    "for x in mytext:\n",
    "    if \"e\" in x:\n",
    "        count += 1\n",
    "        \n",
    "print(\"'e' is repeated\",count, \"times\")\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "#### 3. User Input as Integer"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "The user input is taken as \"b\" and compared to the variable \"a\"."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {
    "collapsed": false
   },
   "outputs": [],
   "source": [
    "a = 5\n",
    "b = int(input(\"Give me a number:\"))\n",
    "if b == a:\n",
    "    print(\"Yes, right\")\n",
    "else:\n",
    "    print(\"No, No..!\")"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "#### 4. Open and Read Files "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "First create a file named \"ques.txt\" and enter some questions in it. Read the file then in your Python code. Consider that it is an interview and you need to register the time as well. Ask the person name first and then save the file under his name."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {
    "collapsed": false
   },
   "outputs": [],
   "source": [
    "import datetime\n",
    "file = open('ques.txt', 'r')\n",
    "username = input(\"What is your name? \")\n",
    "myfile = open(username+\".txt\", \"a\")\n",
    "myfile.close()\n",
    "output = open(username+\".txt\", \"r+\")\n",
    "for line in file:\n",
    "    the_reply = input(line)\n",
    "    line1= line+\"{0}: {1} \\n\".format(username, the_reply)\n",
    "    output.write(line1)\n",
    "\n",
    "output.write(\"\\n\")\n",
    "output.write(\"Interview Time: \"+str(datetime.datetime.now().time()))  \n",
    "output.close()"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "#### 5. Read a File "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "collapsed": true
   },
   "source": [
    "Read the file that you created line by line with answers from the interviewee. "
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {
    "collapsed": true
   },
   "outputs": [],
   "source": [
    "file = open(\"User.txt\", \"r\")\n",
    "mylines = file.readlines()\n",
    "\n",
    "for line in mylines:\n",
    "    my_next = mylines.index(line)+1\n",
    "    if \"How old are you?\" in line:\n",
    "        print(mylines[my_next])\n",
    "    if \"What is your job?\" in line:\n",
    "        print(mylines[my_next])\n",
    "    if \"Where are you from?\" in line:\n",
    "        print(mylines[my_next])\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "#### 6. Adding Answers to Dictionary"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Create an empty dictionary and add the questions and answers to it. "
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {
    "collapsed": true
   },
   "outputs": [],
   "source": [
    "file = open(\"User.txt\", \"r\")\n",
    "mylines = file.readlines()\n",
    "mydict = {}\n",
    "for line in mylines:\n",
    "    my_next = mylines.index(line)+1\n",
    "    if \"How old are you?\" in line:\n",
    "        mydict[mylines[my_next]]=mylines.index(line)\n",
    "    if \"What is your job?\" in line:\n",
    "        mydict[mylines[my_next]]=mylines.index(line)\n",
    "    if \"Where are you from?\" in line:\n",
    "        mydict[mylines[my_next]]=mylines.index(line)\n",
    "\n",
    "print(mydict)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "#### 7. Sort the Dictionary"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "To know how to sort the dict. "
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {
    "collapsed": false
   },
   "outputs": [],
   "source": [
    "file = open(\"User.txt\", \"r\")\n",
    "mylines = file.readlines()\n",
    "\n",
    "mydict = {}\n",
    "for line in mylines:\n",
    "    my_line = line.replace(\"\\n\", \"\")\n",
    "    mydict[my_line]=mylines.index(line)\n",
    "\n",
    "\n",
    "print(sorted(mydict.items(), key=lambda x: x[1]))\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "#### 8. How to Run a Flask Webserver"
   ]
  },
  {
   "cell_type": "raw",
   "metadata": {},
   "source": [
    "A very simple web page with Flask which resolves in port 5000. Name the file \"hello.py\" and then run it with following commands:\n",
    "\n",
    "$ export FLASK_APP=hello.py\n",
    "$ flask run\n",
    "\n",
    "(public access: flask run --host=0.0.0.0)\n",
    "\n",
    "Quick start can be found here: http://flask.pocoo.org/docs/0.12/quickstart/\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {
    "collapsed": false
   },
   "outputs": [],
   "source": [
    "from flask import Flask\n",
    "from flask import request\n",
    "\n",
    "app = Flask(__name__)\n",
    "\n",
    "@app.route('/')\n",
    "def index():\n",
    "    return 'Welcome'\n",
    "    \n",
    "@app.route('/login')\n",
    "def login():\n",
    "    username = request.args.get('username')\n",
    "    password = request.args.get('password')\n",
    "    return '%s is' %username\n",
    "\n",
    "@app.route('/user/<username>')\n",
    "def show_user_profile(username):\n",
    "    # show the user profile for that user\n",
    "    return '<html><body>This is a tes to see if <span style=\"font-weight:bold\">%s</span> is shown in middle of html text</body></html>' % username\n",
    "\n",
    "@app.route('/post/<int:post_id>')\n",
    "def show_post(post_id):\n",
    "    # show the post with the given id, the id is an integer\n",
    "    return 'Post %d' % post_id\n",
    "\n",
    "@app.route('/test')\n",
    "def test():\n",
    "    return 'this is a test'\n",
    "\n",
    "\n",
    "if __name__ == '__main__':\n",
    "    app.run(host='127.0.0.1', port=5000)\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "#### 9. Command Line Arguments"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "To run the code, type in the command line: \n",
    "\n",
    "$ python test.py arg1 arg2 arg3\n",
    "\n",
    "in which arguments can be for example \"user1.txt\" \"user2.txt\", etc\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {
    "collapsed": false
   },
   "outputs": [],
   "source": [
    "#!/usr/bin/python\n",
    "import sys\n",
    " \n",
    "# Get the total number of args passed to the demo.py\n",
    "total = len(sys.argv)\n",
    " \n",
    "# Get the arguments list \n",
    "cmdargs = str(sys.argv)\n",
    " \n",
    "# Print it\n",
    "print (\"The total numbers of args passed to the script: %d \" % total)\n",
    "print (\"Args list: %s \" % cmdargs)\n",
    "mydict = {}\n",
    "excepts = sys.argv[0]\n",
    "sys.argv.remove(excepts)\n",
    "\n",
    "for x in sys.argv:\n",
    "    print(x, end=\" \")\n",
    "    file = open(x, \"r\")\n",
    "    f = file.readlines()\n",
    "    for line in f:\n",
    "        print(line, end=\" \")"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "#### 10. Making Dictionary from a Text File"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "NLTK tokenizer is used to separate the sentences. The structure is somehow what I need. It should be completed!"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {
    "collapsed": false
   },
   "outputs": [],
   "source": [
    "import glob\n",
    "from nltk.tokenize import sent_tokenize\n",
    "\n",
    "my_files = glob.glob('Arsam.txt')\n",
    "mylist = []\n",
    "for i in my_files:\n",
    "    file = open(i, 'r')\n",
    "    data = file.read()\n",
    "    sent_tokenize_list = sent_tokenize(data)\n",
    "    count = len(sent_tokenize_list)\n",
    "    mylist.append(i)\n",
    "    for x in range(count):\n",
    "        myformat = (sent_tokenize_list[x],'MX')\n",
    "        mylist.append(myformat)\n",
    "\n",
    "    print(mylist)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "#### 11. A bit of Node.Js (Sorry Python)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Save the code as \"server.js\" and run it with:\n",
    "    \n",
    "    $ node server.js\n",
    "    "
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {
    "collapsed": false
   },
   "outputs": [],
   "source": [
    "var express = require('express');\n",
    "var app = express();\n",
    "\n",
    "app.get('/', function (req, res) {\n",
    "   res.send('Hello World');\n",
    "})\n",
    "\n",
    "var server = app.listen(8081, function () {\n",
    "   var host = server.address().address\n",
    "   var port = server.address().port\n",
    "   \n",
    "   console.log(\"Example app listening at http://%s:%s\", host, port)\n",
    "})"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "#### 12. Extract Links from a URL "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Using BeautifulSoup"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {
    "collapsed": false
   },
   "outputs": [],
   "source": [
    "import urllib2\n",
    "from bs4 import BeautifulSoup\n",
    "url = urllib2.urlopen(\"http://aclanthology.info/\").read()\n",
    "soup = BeautifulSoup(url)\n",
    "for line in soup.find_all('bib'):\n",
    "    print(line.get('href'))"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "#### 13. Idiomic Python"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Some practices for loop through data in the lists"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {
    "collapsed": false
   },
   "outputs": [],
   "source": [
    "z = [ 'a', 'b', 'c', 'd' ]\n",
    "i = 0\n",
    "while i < len(z):\n",
    "    print(i, z[i])\n",
    "    i += 1\n",
    "    \n",
    "#adds a line between results\n",
    "print()\n",
    "\n",
    "for i in range(0, len(z)):\n",
    "    print(i, z[i])\n",
    "\n",
    "#adds a line between results\n",
    "print()    \n",
    "\n",
    "\n",
    "for i, item in enumerate(z):\n",
    "    print(i, item)\n",
    "\n",
    "#adds a line between results\n",
    "print()"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "#### 14. Fun with dictionary"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 8,
   "metadata": {
    "collapsed": false
   },
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "{'a': 5, 'b': 4, 'c': 18}\n"
     ]
    }
   ],
   "source": [
    "e = dict(a=5, b=4, c=18)\n",
    "print(e)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "and more"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 9,
   "metadata": {
    "collapsed": false
   },
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "{'a': 5, 'b': 4, 'c': 18}\n"
     ]
    }
   ],
   "source": [
    "d = {}\n",
    "d['a'] = 5\n",
    "d['b'] = 4\n",
    "d['c'] = 18\n",
    "print(d)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "and even more"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 12,
   "metadata": {
    "collapsed": false
   },
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "dict_items([('a', 5), ('b', 4), ('c', 18)])\n"
     ]
    }
   ],
   "source": [
    "items = d.items()\n",
    "print(items)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "and get them sorted"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 17,
   "metadata": {
    "collapsed": false
   },
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "dict_items([('a', 5), ('b', 4), ('c', 18)])\n"
     ]
    }
   ],
   "source": [
    "sorted(items)\n",
    "print(items)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "collapsed": true
   },
   "source": [
    "#### 15. Calculating \"Average\" and \"Standard Division\" for a list"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 19,
   "metadata": {
    "collapsed": false
   },
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "3.0 +/- 1.4142135623730951\n"
     ]
    }
   ],
   "source": [
    "import math\n",
    "data = [ 1, 2, 3, 4, 5 ]\n",
    "average = sum(data) / float(len(data))\n",
    "stddev = sum([ (x - average)**2 for x in data ]) / float(len(data))\n",
    "stddev = math.sqrt(stddev)\n",
    "print(average, '+/-', stddev)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {
    "collapsed": true
   },
   "outputs": [],
   "source": []
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python 3",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.6.0"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 2
}

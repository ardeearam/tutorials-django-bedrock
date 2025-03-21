```
  # Prepare Amazon Bedrock Knowledge Bases

  # Prepare the data
  # Create a helper task that gets a URL, and removes HTML tags
  # tutorial-django-bedrock/
  python app/app/lib/url_to_text.py https://lawphil.net/statutes/repacts/ra1949/ra_386_1949.html > knowledge_base/ra386.txt
  python app/app/lib/split_act_into_articles.py knowledge_base/ra386.txt knowledge_base
  rm knowledge_base/ra386.txt       # Do not include the whole text - results will be redundant
  aws s3 cp . s3://tutorial-django-bedrock --recursive --profile dev

  # Tweak the LLM prompt
  # Test Bedrock Knowledge Base in Console to see if it is sane

  # Summary of the RAG system - what we have so far

  # Create the python code that will connect to Amazon Bedrock

  mkdir tutorial-django-bedrock
  cd tutorial-django-bedrock
  python3 -m venv venv
  source venv/bin/activate

  pip install django boto3
  pip freeze > requirements.txt

  django-admin startproject app .
  python manage.py runserver

  # Add a minimal frontend

  # create views.py
  # app/urls.py - add route to home
  # app/settings.py - add apps to INSTALLED_APPS 
  # app/templates/app/index.html

  # Add backend

  # app/views.py
  # app/lib/bedrock.py

  # Ensure AWS Profile is set properly
  aws configure sso
  export AWS_POFILE=dev







```
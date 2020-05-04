.. _pupa-getting-started:


pupa
====

Pupa is a legislative data scraping framework. This framework allows users to create their own specified scrapers.


pupa.cli
========

* dbinit    - initializes a postgres database for use with pupa scrapers

* init      - initializes a local project directory ready for people to write scrapers

* update    - updates data, can be run with --scrape if desire is to examine data locally

pupa.scrape
===========

scrape.Scraper - base class for all scrapers

    self.info
    self.debug
    self.warning
    self.error
    self.critical

    self.save_object(obj) - given a scrape object saves it to disk
        calls obj.pre_save(jid), obj.as_dict(), and obj.validate()

    self.do_scrape(**kwargs) - the workhorse of the scraper, runs a scrape by calling self.scrape()
        passed on all arbitrary args to scrape, which can use them for discrimination

    self.scrape(**kwargs) - the user-implemented method where the scraper should be implemented


pupa options 
============

session: Option to scrape data based upon a specific session

chamber: Option to scrape data based upon a specific chamber

prefiles: Option to scrape data before a specified session

start/end dates: Option to scrape based upon date restrictions
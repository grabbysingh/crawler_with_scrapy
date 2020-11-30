# -*- coding: utf-8 -*-
"""
Created on Mon Nov 30 09:59:49 2020

@author: gaura
"""

import scrapy
from ..items import AmazonscrapItem

class ClassName(scrapy.Spider):
    name = '' #1
    page_number = 2
    start_urls = [
        '' #2
    ]

    def FunctionName(self, response):
        items = AmazonscrapItem()
        all = response.css('') #3

        for a in all:
            head = a.css('').css('').extract() #4
            para = a.css('').css('').extract() #5

            items['head'] = head
            items['para'] = para

            yield items

            next_page = '' + str(ClassName.page_number) #6
            if ClassName.page_number <= 100: #7
                ClassName.page_number += 1
                yield response.follow(next_page, callback=self.FunctionName)
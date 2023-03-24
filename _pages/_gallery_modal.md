---
layout: page
permalink: /photography-modal/
title: photography-modal
description: a collection of photos from past adventures.
nav: true
nav_order: 4
folder: "/img/gallery/images"
---

<div class="container">
    <div class ="image-gallery">
        {% assign sorted = site.static_files | sort: 'date' | reverse %}
        {% for file in sorted %}
        {% if file.path contains page.folder %}
        {% if file.extname == '.JPG' or file.extname == '.jpg' or file.extname == '.png' %}
            {% assign filenameparts = file.path | split: "/" %}
            {% assign filename = filenameparts | last | replace: file.extname,"" %}
                <div class="box">
                    <a href="#" class="" data-toggle="modal" data-target="#carouselModal" data-slide-to="{{ forloop.index0 }}">
                        <img src="{{ site.thumbsurl }}{{file.name }}" alt="{{ filename }}"  class="img-gallery" />
                    </a>
                </div>
            {% endif %}
            {% endif %}
        {% endfor %}
    </div>

  <!-- modal -->
  <div class="modal fade" id="carouselModal" tabindex="-1" role="dialog" aria-labelledby="basicModal" aria-hidden="true">
    <div class="modal-dialog modal-lg">
      <div class="modal-content">
           <!-- carousel -->
            <div id="carouselExampleSlidesOnly" class="carousel slide" data-ride="carousel">
                <div class="carousel-inner">
                {% assign sorted = site.static_files | sort: 'date' | reverse %}
                {% for file in sorted %}
                {% if file.path contains page.folder %}
                {% if file.extname == '.JPG' or file.extname == '.jpg' or file.extname == '.png' %}
                    {% assign filenameparts = file.path | split: "/" %}
                    {% assign filename = filenameparts | last | replace: file.extname,"" %}
                        <div class="carousel-item" data-ftype="Image">
                        <img src="{{ file.path | relative_url }}" alt="{{ filename }}"  class="d-block w-100" />
                        </div>
                    {% endif %}
                    {% endif %}
                {% endfor %}
                </div>
                <a class="carousel-control-prev" href="#carouselExampleControls" role="button" data-slide="prev">
                <span class="carousel-control-prev-icon" aria-hidden="true"></span>
                <span class="sr-only">Previous</span>
                </a>
                <a class="carousel-control-next" href="#carouselExampleControls" role="button" data-slide="next">
                <span class="carousel-control-next-icon" aria-hidden="true"></span>
                <span class="sr-only">Next</span>
                </a>
            </div>
      </div>
    </div>
  </div>

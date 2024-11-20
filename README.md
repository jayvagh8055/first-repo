# first-repo
hello 
how are you
## make model.py like this rom django.db import models
from app_modules.base.models import BaseModel
# Create your models here.

class LanguageLevel(BaseModel):
    name = models.CharField(max_length=255)
    status = models.BooleanField(default=False)
    
    def __str__(self):
        return self.name
##make forms.py like this from django import forms 
from app_modules.adminapp import models


class LanguageLevelForm(forms.ModelForm):
    class Meta:
        model = models.LanguageLevel
        fields = "__all__"

3) view.py like this
# ----------------------------------------- LANGUAGE_LEVEL CRUD ----------------------------------------------------------------

class LanguageLevelCreateView(CreateView):
    model = models.LanguageLevel
    form_class = forms.LanguageLevelForm
    template_name = "adminapp/languagelevel_add.html"
    success_url = reverse_lazy("adminapp:languagelevellist")
    
    
class LanguageLevelListView(ListView):
    model = models.LanguageLevel
    template_name = "adminapp/languagelevel_list.html"
    
    
class LanguageLevelUpdateView(UpdateView):
    model = models.LanguageLevel
    form_class = forms.LanguageLevelForm
    template_name = "adminapp/languagelevel_update.html"
    success_url = reverse_lazy("adminapp:languagelevellist")
        
   
class LanguageLevelDeleteView(DeleteView):
    model = models.LanguageLevel
    template_name = "adminapp/languagelevel_list.html"
    success_url = reverse_lazy("adminapp:languagelevellist")

    ================================================================================================================
    
4) make template 3 add,list,update

hear make master.html
<!DOCTYPE html>
<html lang="en">
  {% load static %}
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <link rel="stylesheet" href="{% static 'adminapp/css/style.css' %}" />
    <link
      href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/css/bootstrap.min.css"
      rel="stylesheet"
      integrity="sha384-EVSTQN3/azprG1Anm3QDgpJLIm9Nao0Yz1ztcQTwFspd3yD65VohhpuuCOmLASjC"
      crossorigin="anonymous"
    />
    <!-- <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css"> -->
    <link
      rel="stylesheet"
      href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css"
    />
    <link
      rel="stylesheet"
      href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css"
    />
    <script
      src="https://kit.fontawesome.com/yourcode.js"
      crossorigin="anonymous"
    ></script>
  </head>
  <body
    class="page-header-fixed page-sidebar-closed-hide-logo page-content-white"
  >
    <!-- BEGIN HEADER -->

    <div class="page-header navbar navbar-fixed-top">
      <!-- BEGIN HEADER INNER -->

      <div class="page-header-inner">
        <!-- BEGIN LOGO -->

        <div class="page-logo">
          <a>
            <img
              src="https://www.sharjeelanjum.com/demos/jobsportal-update/sitesetting_images/thumb/jobs-portal-1614227396-847.png"
              alt="logo"
              style="max-width: 170px; max-height: 40px"
            />
            <!-- class="logo-default" --></a
          >

          <div class="menu-toggler sidebar-toggler"></div>
        </div>

        <!-- END LOGO -->

        <!-- BEGIN RESPONSIVE MENU TOGGLER -->

        <a
          href="javascript:;"
          class="menu-toggler responsive-toggler"
          data-toggle="collapse"
          data-target=".navbar-collapse"
        >
        </a>

        <!-- END RESPONSIVE MENU TOGGLER -->

        <!-- BEGIN TOP NAVIGATION MENU -->

        <div class="top-menu">
          <ul class="nav navbar-nav pull-right">
            <!-- BEGIN USER LOGIN DROPDOWN -->
            <!-- DOC: Apply "dropdown-dark" class after below "dropdown-extended" to change the dropdown styte -->
            <li class="dropdown dropdown-user">
              <a
                href="javascript:;"
                class="dropdown-toggle"
                data-toggle="dropdown"
                data-hover="dropdown"
                data-close-others="true"
              >
                <span class="username username-hide-on-mobile"> Buyer </span>
                <i class="fa fa-angle-down"></i>
              </a>
              <ul class="dropdown-menu dropdown-menu-default">
                <li>
                  <a> <i class="icon-user"></i> My Profile </a>
                </li>
                <li class="divider"></li>
                <li>
                  <a
                    href="https://www.sharjeelanjum.com/demos/jobsportal-update/admin/logout"
                  >
                    <i class="icon-key"></i> Log Out
                  </a>
                </li>
              </ul>
            </li>
            <!-- END USER LOGIN DROPDOWN -->
            <li class="dropdown dropdown-quick-sidebar-toggler">
              <a
                href="https://www.sharjeelanjum.com/demos/jobsportal-update/admin/logout"
                class="dropdown-toggle"
              >
                <i class="icon-logout"></i>
              </a>
            </li>
          </ul>
        </div>

        <!-- END TOP NAVIGATION MENU -->
      </div>

      <!-- END HEADER INNER -->
    </div>

    <!-- END HEADER -->

    <!-- BEGIN HEADER & CONTENT DIVIDER -->

    <div class="clearfix"></div>

    <!-- END HEADER & CONTENT DIVIDER -->

    <!-- BEGIN CONTAINER -->

    <div class="page-container">
      <!-- BEGIN SIDEBAR -->

      <div class="page-sidebar-wrapper">
        <ul
          class="page-sidebar-menu page-header-fixed"
          data-keep-expanded="false"
          data-auto-scroll="true"
          data-slide-speed="200"
        >
          <li class="sidebar-toggler-wrapper hide">
            <div class="sidebar-toggler"></div>
          </li>
          <li class="sidebar-search-wrapper"></li>
          <li class="nav-item start active">
            <a href="./Mydashboard.html" class="nav-link white-text">
              <i class="icon-home"></i> <span class="title">Dashboard</span>
            </a>
          </li>
          <li class="heading">
            <h3 class="uppercase">Admin Users</h3>
          </li>
          <li class="nav-item">
            <a
              href="javascript:;"
              class="nav-link white-text nav-toggle"
              data-bs-toggle="collapse"
              data-bs-target="#collapseadmin"
              aria-expanded="false"
            >
              <i class="fa fa-user"></i> <span class="title">Admin Users</span>
              <span class="arrow"></span>
            </a>
            <ul class="collapse" id="collapseadmin">
              <li class="nav-item">
                <a class="nav-link white-text">
                  <i class="fa fa-user"></i>
                  <span class="title">List All Admin Users</span>
                </a>
              </li>
              <li class="nav-item">
                <a class="nav-link white-text">
                  <i class="fa fa-users"></i>
                  <span class="title">Add Admin User</span>
                </a>
              </li>
            </ul>
          </li>

          <li class="heading">
            <h3 class="uppercase">Modules</h3>
          </li>
          <li class="nav-item">
            <a
              href="javascript:;"
              class="nav-link white-text nav-toggle"
              data-bs-toggle="collapse"
              data-bs-target="#collapsejob"
              aria-expanded="false"
            >
              <i class="fas fa-briefcase"></i> <span class="title">Jobs</span>
              <span class="arrow"></span>
            </a>
            <ul class="collapse" id="collapsejob">
              <li class="nav-item">
                <a class="nav-link white-text">
                  <span class="title">List Jobs</span>
                </a>
              </li>
              <li class="nav-item">
                <a class="nav-link white-text">
                  <span class="title">Add new Job</span>
                </a>
              </li>
            </ul>
          </li>
          <li class="nav-item">
            <a
              href="javascript:;"
              class="nav-link white-text nav-toggle"
              data-bs-toggle="collapse"
              data-bs-target="#collapsecompanies"
              aria-expanded="false"
            >
              <i class="fa fa-building"></i>
              <span class="title">Companies</span> <span class="arrow"></span>
            </a>

            <ul class="collapse" id="collapsecompanies">
              <li class="nav-item">
                <a class="nav-link white-text">
                  <span class="title">List Companies</span>
                </a>
              </li>

              <li class="nav-item">
                <a class="nav-link white-text">
                  <span class="title">Add new Company</span>
                </a>
              </li>
              <li class="nav-item">
                <a class="nav-link white-text">
                  <span class="title">List Companies Payment History</span>
                </a>
              </li>
            </ul>
          </li>
          <li class="nav-item">
            <a
              href="javascript:;"
              class="nav-link white-text nav-toggle"
              data-bs-toggle="collapse"
              data-bs-target="#collapseuserprofile"
              aria-expanded="false"
            >
              <i class="fa fa-user"></i>
              <span class="title">User Profiles</span>
              <span class="arrow"></span>
            </a>
            <ul class="collapse" id="collapseuserprofile">
              <li class="nav-item">
                <a class="nav-link white-text">
                  <i class="fa fa-users"></i>
                  <span class="title">List User Profiles</span>
                </a>
              </li>
              <li class="nav-item">
                <a href="./Add_new_user.html" class="nav-link white-text">
                  <i class="fa fa-user"></i>
                  <span class="title">Add new User Profile</span>
                </a>
              </li>
            </ul>
          </li>
          <li class="nav-item">
            <a
              href="javascript:;"
              class="nav-link white-text nav-toggle"
              data-bs-toggle="collapse"
              data-bs-target="#collapsecms"
              aria-expanded="false"
            >
              <i class="fa fa-file-text-o" aria-hidden="true"></i>
              <span class="title">C.M.S</span> <span class="arrow"></span>
            </a>
            <ul class="collapse" id="collapsecms">
              <li class="nav-item">
                <a class="nav-link white-text">
                  <span class="title">List C.M.S Pages</span>
                </a>
              </li>
              <li class="nav-item">
                <a class="nav-link white-text">
                  <span class="title">Add new C.M.S Page</span>
                </a>
              </li>
              <li class="nav-item">
                <a class="nav-link white-text">
                  <span class="title">List Translated Pages</span>
                </a>
              </li>
              <li class="nav-item">
                <a class="nav-link white-text">
                  <span class="title">Add new Translate Page</span>
                </a>
              </li>
            </ul>
          </li>
          <li class="nav-item">
            <a
              href="javascript:;"
              class="nav-link white-text nav-toggle"
              data-bs-toggle="collapse"
              data-bs-target="#collapseblogs"
              aria-expanded="false"
            >
              <i class="fa fa-level-up" aria-hidden="true"></i>
              <span class="title">Manage Blogs</span>
              <span class="arrow"></span>
            </a>
            <ul class="collapse" id="collapseblogs">
              <li class="nav-item">
                <a class="nav-link white-text">
                  <span class="title">List Blogs</span>
                </a>
              </li>
              <li class="nav-item">
                <a class="nav-link white-text">
                  <span class="title">Add Blog</span>
                </a>
              </li>
              <li class="nav-item">
                <a class="nav-link white-text">
                  <span class="title">Categories</span>
                </a>
              </li>
            </ul>
          </li>
          <li class="nav-item">
            <a
              href="javascript:;"
              class="nav-link white-text nav-toggle"
              data-bs-toggle="collapse"
              data-bs-target="#collapseseo"
              aria-expanded="false"
            >
              <i class="fa fa-line-chart" aria-hidden="true"></i>
              <span class="title">S.E.O</span> <span class="arrow"></span>
            </a>
            <ul class="collapse" id="collapseseo">
              <li class="nav-item">
                <a class="nav-link white-text">
                  <span class="title">List Pages</span>
                </a>
              </li>
            </ul>
          </li>

          <li class="heading">
            <h3 class="uppercase">Manage</h3>
          </li>
          <li class="nav-item">
            <a
              href="javascript:;"
              class="nav-link white-text nav-toggle"
              data-bs-toggle="collapse"
              data-bs-target="#collapsesitesetting"
              aria-expanded="false"
            >
              <i class="icon-wrench"></i>
              <span class="title">Site Settings</span>
              <span class="arrow"></span>
            </a>
            <ul class="collapse" id="collapsesitesetting">
              <li class="nav-item">
                <a class="nav-link white-text">
                  <span class="title">Manage Site Settings</span>
                </a>
              </li>
            </ul>
          </li>

          <li class="heading">
            <h3 class="uppercase">JOB ATTRIBUTES</h3>
          </li>
          <li class="nav-item">
            <a
              href="javascript:;"
              class="nav-link white-text nav-toggle"
              data-bs-toggle="collapse"
              data-bs-target="#collapsesitesetting1"
              aria-expanded="false"
            >
              <i class="icon-wrench"></i>
              <span class="title">Language Levels</span>
              <span class="arrow"></span>
            </a>
            <ul class="collapse" id="collapsesitesetting1">
              <li class="nav-item">
                <a
                  class="nav-link white-text"
                  href="{% url 'adminapp:languagelevellist' %}"
                  ><span class="title">List Language Levels</span></a
                >
                <a
                  class="nav-link white-text"
                  href="{% url 'adminapp:languageleveladd' %}"
                  ><span class="title">Add Language Levels</span></a
                >
              </li>
            </ul>
          </li>
            <li class="nav-item">
            <a
              href="javascript:;"
              class="nav-link white-text nav-toggle"
              data-bs-toggle="collapse"
              data-bs-target="#collapsesitesetting10"
              aria-expanded="false"
            >
              <i class="icon-wrench"></i>
              <span class="title">Job Shift</span>
              <span class="arrow"></span>
            </a>
            <ul class="collapse" id="collapsesitesetting10">
              <li class="nav-item">
                <a
                  class="nav-link white-text"
                  href="{% url 'adminapp:jobshiftlist' %}"
                  ><span class="title">List Job Shift</span></a
                >
                <a
                  class="nav-link white-text"
                  href="{% url 'adminapp:jobshiftadd' %}"
                  ><span class="title">Add Job Shift</span></a
                >
              </li>
            </ul>
          </li>
          <li class="nav-item">
            <a
              href="javascript:;"
              class="nav-link white-text nav-toggle"
              data-bs-toggle="collapse"
              data-bs-target="#collapsesitesetting9"
              aria-expanded="false"
            >
              <i class="icon-wrench"></i>
              <span class="title">Job Type</span>
              <span class="arrow"></span>
            </a>
            <ul class="collapse" id="collapsesitesetting9">
              <li class="nav-item">
                <a
                  class="nav-link white-text"
                  href="{% url 'adminapp:jobtypelist' %}"
                  ><span class="title">List Job Type</span></a
                >
                <a
                  class="nav-link white-text"
                  href="{% url 'adminapp:jobtypeadd' %}"
                  ><span class="title">Add Job Type</span></a
                >
              </li>
            </ul>
          </li>
          <li class="nav-item">
            <a
              href="javascript:;"
              class="nav-link white-text nav-toggle"
              data-bs-toggle="collapse"
              data-bs-target="#collapsesitesetting11"
              aria-expanded="false"
            >
              <i class="icon-wrench"></i>
              <span class="title">Degree Levels</span>
              <span class="arrow"></span>
            </a>
            <ul class="collapse" id="collapsesitesetting11">
              <li class="nav-item">
                <a
                  class="nav-link white-text"
                  href="{% url 'adminapp:degreelevellist' %}"
                  ><span class="title">List Language Levels</span></a
                >
                <a
                  class="nav-link white-text"
                  href="{% url 'adminapp:degreeleveladd' %}"
                  ><span class="title">Add Language Levels</span></a
                >
              </li>
            </ul>
          </li>
           <li class="nav-item">
            <a
              href="javascript:;"
              class="nav-link white-text nav-toggle"
              data-bs-toggle="collapse"
              data-bs-target="#collapsesitesetting12"
              aria-expanded="false"
            >
              <i class="icon-wrench"></i>
              <span class="title">DegreeType</span>
              <span class="arrow"></span>
            </a>
            <ul class="collapse" id="collapsesitesetting12">
              <li class="nav-item">
                <a
                  class="nav-link white-text"
                  href="{% url 'adminapp:degreetypelist' %}"
                  ><span class="title">List Degree Type</span></a
                >
                <a
                  class="nav-link white-text"
                  href="{% url 'adminapp:degreetypeadd' %}"
                  ><span class="title">Add Degree Type</span></a
                >
              </li>
            
            </ul>
          </li>
          <li class="nav-item">
            <a
              href="javascript:;"
              class="nav-link white-text nav-toggle"
              data-bs-toggle="collapse"
              data-bs-target="#collapsesitesetting13"
              aria-expanded="false"
            >
              <i class="icon-wrench"></i>
              <span class="title">Major Subject</span>
              <span class="arrow"></span>
            </a>
            <ul class="collapse" id="collapsesitesetting13">
              <li class="nav-item">
                <a
                  class="nav-link white-text"
                  href="{% url 'adminapp:majorsubjectlist' %}"
                  ><span class="title">List Major Suibject</span></a
                >
                <a
                  class="nav-link white-text"
                  href="{% url 'adminapp:majorsubjectadd' %}"
                  ><span class="title">Add Major Suibject</span></a
                >
              </li>
            </ul>
          </li>
          <li class="nav-item">
            <a
              href="javascript:;"
              class="nav-link white-text nav-toggle"
              data-bs-toggle="collapse"
              data-bs-target="#collapsesitesetting14"
              aria-expanded="false"
            >
              <i class="icon-wrench"></i>
              <span class="title">ResultType</span>
              <span class="arrow"></span>
            </a>
            <ul class="collapse" id="collapsesitesetting14">
              <li class="nav-item">
                <a
                  class="nav-link white-text"
                  href="{% url 'adminapp:resulttypelist' %}"
                  ><span class="title">List ResultType</span></a
                >
                <a
                  class="nav-link white-text"
                  href="{% url 'adminapp:resulttypeadd' %}"
                  ><span class="title">Add ResultType</span></a
                >
              </li>
            </ul>
          </li>
          <li class="nav-item">
            <a
              href="javascript:;"
              class="nav-link white-text nav-toggle"
              data-bs-toggle="collapse"
              data-bs-target="#collapsesitesetting15"
              aria-expanded="false"
            >
              <i class="icon-wrench"></i>
              <span class="title">MaritialStatus</span>
              <span class="arrow"></span>
            </a>
            <ul class="collapse" id="collapsesitesetting15">
              <li class="nav-item">
                <a
                  class="nav-link white-text"
                  href="{% url 'adminapp:maritialstatuslist' %}"
                  ><span class="title">List Maritial Status</span></a
                >
                <a
                  class="nav-link white-text"
                  href="{% url 'adminapp:maritialstatusadd' %}"
                  ><span class="title">Add Maritial Status</span></a
                >
              </li>
            </ul>
          </li>
           <li class="nav-item">
            <a
              href="javascript:;"
              class="nav-link white-text nav-toggle"
              data-bs-toggle="collapse"
              data-bs-target="#collapsesitesetting16"
              aria-expanded="false"
            >
              <i class="icon-wrench"></i>
              <span class="title">OwnerShip Type</span>
              <span class="arrow"></span>
            </a>
            <ul class="collapse" id="collapsesitesetting16">
              <li class="nav-item">
                <a
                  class="nav-link white-text"
                  href="{% url 'adminapp:ownershiptypelist' %}"
                  ><span class="title">List OwnerShip Type</span></a
                >
                <a
                  class="nav-link white-text"
                  href="{% url 'adminapp:ownershiptypeadd' %}"
                  ><span class="title">Add OwnerShip Type</span></a
                >
              </li>
            </ul>
          </li>
           <li class="nav-item">
            <a
              href="javascript:;"
              class="nav-link white-text nav-toggle"
              data-bs-toggle="collapse"
              data-bs-target="#collapsesitesetting17"
              aria-expanded="false"
            >
              <i class="icon-wrench"></i>
              <span class="title">Salary Period</span>
              <span class="arrow"></span>
            </a>
            <ul class="collapse" id="collapsesitesetting17">
              <li class="nav-item">
                <a
                  class="nav-link white-text"
                  href="{% url 'adminapp:salaryperiodlist' %}"
                  ><span class="title">List Salary Period</span></a
                >
                <a
                  class="nav-link white-text"
                  href="{% url 'adminapp:salaryperiodadd' %}"
                  ><span class="title">Add Salary Period</span></a
                >
              </li>
            </ul>
          </li>
         
        </ul>
        </ul>

      </div>

      <!-- END SIDEBAR -->
      {% block content %} {% endblock %}
    </div>
    <!-- END CONTAINER -->
    <!-- BEGIN FOOTER -->
    <div class="page-footer">
      <div class="page-footer-inner">
        2024 © JOBS PORTAL Updated. Admin Panel.
      </div>
      <div class="scroll-to-top"><i class="icon-arrow-up"></i></div>
    </div>
    <!-- END FOOTER -->
    {% block script %} {% endblock script %}
    <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
    <script
      src="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/js/bootstrap.bundle.min.js"
      integrity="sha384-MrcW6ZMFYlzcLA8Nl+NtUVF0sA7MsXsP1UyJoMp4YLEuNSfAP+JcXn/tWtIaxVXM"
      crossorigin="anonymous"
    ></script>
  </body>
</html>
-----------------------------------------------------------------------------------------------------------
 - add temlate.html
{% extends 'adminapp/master.html' %}
{% load static %}
{% block content %}

    <div class="page-content-wrapper"> 
        <div class="page-content" style="background-color:#eef1f5;"> 
            <div class="page-bar">
                <nav aria-label="breadcrumb">
                    <ol class="breadcrumb">
                    <li class="breadcrumb-item"><a href="#">Home</a></li>
                    <li class="breadcrumb-item"><a href="#">Users</a></li>
                    <li class="breadcrumb-item active" aria-current="page">Add Language Level</li>
                    </ol>
                </nav>
            </div>

            <div class="row">
                <div class="col-md-12">
                    <div class="form light bordered">
                        <div class="form-title">
                            <div class="caption"> <i class="fa fa-cog"></i> <span class="caption-subject bold uppercase">Language Level Form</span> </div>
                        </div>
                        <div class="form-body">

                            <ul class="nav nav-tabs mb-5">
                                <li><a class="nav-link active" aria-current="page" href="#">Details</a></li>
                                <li><a class="nav-link" href="#">Summary</a></li>
                                <li><a class="nav-link" href="#">C.V</a></li>
                                <li><a class="nav-link" href="#">Projects</a></li>
                                <li><a class="nav-link" href="#">Experience</a></li>
                                <li><a class="nav-link" href="#">Education</a></li>
                                <li><a class="nav-link" href="#">Skills</a></li>
                                <li><a class="nav-link" href="#">Languages</a></li>
                            </ul>
                            <form method="post" enctype="multipart/form-data">
                                {% csrf_token %}
                                <div class="row">
                                    <div class="col col-sm-6">
                                        <div class="form-group mb-3">
                                            <label for="first_name" class="bold">First Name</label>                    
                                            <input class="form-control" id="first_name" placeholder="First Name" name="name" type="text">
                                        </div>
                                    </div>
                                </div>
                               
                             
                                <div class="col col-sm-4">
                                    <div class="form-group mb-3">
                                        <label for="is_active" class="bold">Active</label>
                                        <div class="radio-list">
                                            <label class="radio-inline">
                                                <div class="radio" id="uniform-active">
                                                    <span class="checked">
                                                        <input id="active" name="status" type="radio" value="1" >
                                                    </span>Active
                                                </div>
                                            </label><br>
                                            <label class="radio-inline">
                                                <div class="radio" id="uniform-not_active">
                                                    <span>
                                                        <input id="not_active" name="status" type="radio" value="0">
                                                    </span>In-Active
                                                </div>
                                            </label>
                                        </div>
                                    </div>
                                </div>
                                <div class="col col-sm-4">
                                    <div class="form-group mb-3">
                                        <label for="verified" class="bold">Is Default ?</label>
                                        <div class="radio-list">
                                            <label class="radio-inline">
                                                <div class="radio" id="uniform-verified">
                                                    <span class="checked">
                                                        <input id="verified" name="verified" type="radio" value="1" checked="&quot;checked&quot;">
                                                    </span>Yes
                                                </div>
                                            </label><br>
                                            <label class="radio-inline">
                                                <div class="radio" id="uniform-not_verified">
                                                    <span>
                                                        <input id="not_verified" name="verified" type="radio" value="0">
                                                    </span>No
                                                </div>
                                            </label>
                                        </div>
                                    </div>
                                </div>
                            </div>
                            <button class="btn btn-large btn-primary mb-3 w-auto" type="submit">Update <i class="fa fa-arrow-circle-right" aria-hidden="true"></i></button> 
                            </form>
                        </div>
                    </div>
            </div>
            <!-- END PAGE MAIN CONTENT INNER -->
            
            
        </div>
    <!-- END CONTENT BODY --> 
    </div>

    {% block script %}
    <script>

        // JavaScript code to display selected image file in the preview
        const input = document.getElementById('image-upload');
               const preview = document.getElementById('image-preview');
             
               input.addEventListener('change', function(event) {
                 const file = this.files[0]; // Get the selected file
                 if (file) {
                   const reader = new FileReader(); // Initialize FileReader object
             
                   reader.onload = function(event) {
                     const img = new Image(); // Create new image element
                     img.onload = function() {
               const maxWidth = 200; // Max width for the image preview
               const maxHeight = 200; // Max height for the image preview
               let width = img.width;
               let height = img.height;
       
               // Calculate new dimensions while maintaining aspect ratio
               if (width > height) {
                 if (width > maxWidth) {
                   height *= maxWidth / width;
                   width = maxWidth;
                 }
               } else {
                 if (height > maxHeight) {
                   width *= maxHeight / height;
                   height = maxHeight;
                 }
               }
       
               // Set the image dimensions
               img.width = width;
               img.height = height;
       
               // Clear any previous preview
               preview.innerHTML = '';
               preview.appendChild(img); // Append the image to the preview div
             };
       
                     img.src = event.target.result; // Set the image source
             
                     // Clear any previous preview
                     preview.innerHTML = '';
                     preview.appendChild(img); // Append the image to the preview div
                   }
             
                   reader.readAsDataURL(file); // Convert file to data URL format
                 } else {
                   preview.innerHTML = ''; // Clear preview if no file selected
                 }
       
                 document.getElementById('confirmbtns').style.display='block';
                 document.getElementById('fileselector').style.display='none';
               });
       
    </script>
    {% endblock script %}
    
{% endblock %}
-----------------------------------------------------------------------------------------------------------
 - html page for _list page

  {% extends 'adminapp/master.html' %}
{% load static %} 
{% block content %}

        <!-- BEGIN CONTENT -->
        <div class="page-content-wrapper">
            <div class="page-content" style="background-color:#eef1f5;">
                <div class="page-bar">
                    <nav aria-label="breadcrumb">
                        <ol class="breadcrumb">
                            <li class="breadcrumb-item"><a href="#">Home</a></li>
                            <li class="breadcrumb-item"><a href="#">Users</a></li>
                        </ol>
                    </nav>
                </div>
                <h2 class="page-title"> Manage Language Levels </h2>
                <div class="row">
                    <div class="col-md-12">
                        <div class="form light bordered">
                            <div class="form-title d-flex justify-content-between bordered mb-3 p-3">
                                <div class="caption">
                                    <i class="fa fa-cog"></i>
                                    <span class="caption-subject bold uppercase">Users Form</span>
                                </div>
                                <div class="actions">
                                    <a href="{% url 'adminapp:languageleveladd' %}" class="btn btn-xs btn-success">
                                        <i class="fa fa-plus"></i> Add Language Levels</a>
                                </div>
                            </div>
                            <div class="form-body form">
                                <div class="row">
                                    <div class="col-md-6 col-sm-6">
                                        <div class="dataTables_length" id="user_datatable_ajax_length"><label> 
                                            <select
                                                    name="user_datatable_ajax_length"
                                                    aria-controls="user_datatable_ajax"
                                                    class="form-control input-sm input-xsmall input-inline">
                                                    <option value="10">10</option>
                                                    <option value="25">25</option>
                                                    <option value="50">50</option>
                                                    <option value="100">100</option>
                                                </select> records </label></div>
                                        </div>
                                        <div class="col-md-6 col-sm-6"></div>
                                        <div id="user_datatable_ajax_processing" class="dataTables_processing"
                                            style="display: none;">Processing...</div>
                                    </div>
                                    <div class="table-scrollable">
                                        <table class="table table-striped table-bordered table-hover dataTable no-footer"
                                            id="user_datatable_ajax" role="grid" aria-describedby="user_datatable_ajax_info"
                                            style="width: 1032px;">
                                            <thead>
                                                <tr role="row" class="filter">
                                                    <td rowspan="1" colspan="1"><input type="text" class="form-control"
                                                            name="id" id="id" autocomplete="off"></td>
                                                    <td rowspan="1" colspan="1"><input type="text" class="form-control"
                                                            name="name" id="name" autocomplete="off"></td>
                                                    
                                                    <td rowspan="1" colspan="1"></td>
                                                </tr>
                                                <tr role="row" class="heading">
                                                    <th class="sorting_desc" tabindex="0"
                                                        aria-controls="user_datatable_ajax" rowspan="1" colspan="1"
                                                        aria-sort="descending"
                                                        aria-label="Id: activate to sort column ascending"
                                                        style="width: 255px;">Id</th>
                                                    <th class="sorting" tabindex="0" aria-controls="user_datatable_ajax"
                                                        rowspan="1" colspan="1"
                                                        aria-label="Name: activate to sort column ascending"
                                                        style="width: 255px;">Name</th>
                                                    
                                                    <th class="sorting_disabled" rowspan="1" colspan="1"
                                                        aria-label="Actions" style="width: 84px;">Actions</th>
                                                </tr>
                                            </thead>
                                            <tbody>
                                                {% for ab in object_list %}
                                                <tr id="user_dt_row_14" role="row" class="odd">
                                                    <td class="sorting_1">{{forloop.counter}}</td>
                                                    <td>{{ab.name}}</td>
                                                    <td>
                                                        <div class="dropdown-extended">
                                                            <button class="btn btn-primary dropdown-toggle" type="button"
                                                                id="actionMenuButton" data-bs-toggle="dropdown"
                                                                aria-expanded="false">
                                                                Action
                                                            </button>
                                                            <ul class="dropdown-menu p-1" style=""
                                                                aria-labelledby="actionMenuButton">
                                                                <li><a class="dropdown-item" href="{% url 'adminapp:languagelevelupdate' ab.id %}"><i class="fa fa-pencil"></i>  Edit</a></li>
                                                                <li><a class="dropdown-item" href=""><i class="fa fa-pencil"></i> View Profile Details</a></li>
                                                                <li><a class="dropdown-item" href="#" onclick="showDeletemodal('{{ ab.id }}')" data-bs-toggle="modal" data-bs-target="#deleteConfirmationModal"><i class="fa fa-trash-o"></i> Delete</a></li>
                                                                <li class="dropdown-item"><input type="checkbox" id="active" title=""> Active</li>
                                                                <li class="dropdown-item"><input type="checkbox" id="verify" title=""> Verified </li>
                                                            </ul>
                                                        </div>
                                                    </td>
                                                </tr>
                                                {% endfor %}
                                            </tbody>
                                        </table>
                                    </div>

                                    <div class="row">
                                        <div class="col-md-5 col-sm-5">
                                            <div class="dataTables_info" id="user_datatable_ajax_info" role="status"
                                                aria-live="polite">Showing 1 to 10 of 10 entries</div>
                                        </div>
                                        <div class="col-md-7 col-sm-7">
                                            <div class="dataTables_paginate paging_bootstrap_number"
                                                id="user_datatable_ajax_paginate">
                                                <ul class="pagination" style="visibility: visible;">
                                                    <li class="prev disabled"><a href="#" title="Prev"><i
                                                                class="fa fa-angle-left"></i></a></li>
                                                    <li class="active"><a href="#">1</a></li>
                                                    <li class="next disabled"><a href="#" title="Next"><i
                                                                class="fa fa-angle-right"></i></a></li>
                                                </ul>
                                            </div>
                                        </div>
                                    </div>
                                </div>

                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <!-- END CONTENT -->

        <!--Delete Button trigger modal -->
        <!-- Modal -->
        <div class="modal fade" id="deleteConfirmationModal" tabindex="-1"
            aria-labelledby="deleteModalLabel" aria-hidden="true">
            <div class="modal-dialog">
                <div class="modal-content">
                    <div class="modal-header">
                        <h5 class="modal-title" id="deleteModalLabel">Modal title</h5>
                        <button type="button" class="btn-close" data-bs-dismiss="modal"
                            aria-label="Close"></button>
                    </div>
                    <div class="modal-body">
                        Are you sure! you want to delete?
                    </div>
                    <div class="modal-footer">
                        <button type="button" class="btn btn-secondary"
                            data-bs-dismiss="modal">Cancel</button>
                        <form id="deleteForm" method="POST" action="" style="display: inline;">
                            {% csrf_token %}
                            <button button="submit" class="btn btn-danger">Delete</a>
                        </form>
                    </div>
                </div>
            </div>
        </div>
        <!-- Modal end-->

        
<script>
    function showDeletemodal(itemId) {
        console.log('Delete button clicked');
        console.log(itemId);
        var deleteUrl = "/adminapp/languageleveldelete/" + itemId + "/";
        $('#deleteForm').attr('action', deleteUrl);
        $('#deleteConfirmationModal').modal('show');
        }
        function showCancelConfirmationModal() {
        $('#deleteConfirmationModal').modal('hide');
    }
</script>
            
{% endblock %}  
-----------------------------------------------------------------------------------------------------------
-make update from in html page

{% extends 'adminapp/master.html' %}
{% load static %}
{% block content %}

    <div class="page-content-wrapper"> 
        <div class="page-content" style="background-color:#eef1f5;"> 
            <div class="page-bar">
                <nav aria-label="breadcrumb">
                    <ol class="breadcrumb">
                    <li class="breadcrumb-item"><a href="#">Home</a></li>
                    <li class="breadcrumb-item"><a href="#">Users</a></li>
                    <li class="breadcrumb-item active" aria-current="page">Update Language Level</li>
                    </ol>
                </nav>
            </div>

            <div class="row">
                <div class="col-md-12">
                    <div class="form light bordered">
                        <div class="form-title">
                            <div class="caption"> <i class="fa fa-cog"></i> <span class="caption-subject bold uppercase">Language Level Update</span> </div>
                        </div>
                        <div class="form-body">

                            <ul class="nav nav-tabs mb-5">
                                <li><a class="nav-link active" aria-current="page" href="#">Details</a></li>
                                <li><a class="nav-link" href="#">Summary</a></li>
                                <li><a class="nav-link" href="#">C.V</a></li>
                                <li><a class="nav-link" href="#">Projects</a></li>
                                <li><a class="nav-link" href="#">Experience</a></li>
                                <li><a class="nav-link" href="#">Education</a></li>
                                <li><a class="nav-link" href="#">Skills</a></li>
                                <li><a class="nav-link" href="#">Languages</a></li>
                            </ul>
                            <form method="post" enctype="multipart/form-data">
                                {% csrf_token %}
                                <div class="row">
                                    <div class="col col-sm-6">
                                        <div class="form-group mb-3">
                                            <label for="first_name" class="bold">First Name</label> 
                                            <input class="form-control" id="first_name" placeholder="First Name" name="name" value="{{ form.name.value}}" type="text">
                                        </div>
                                    </div>
                                </div>
                               
                             
                                <div class="col col-sm-4">
                                    <div class="form-group mb-3">
                                        <label for="is_active" class="bold">Active</label>
                                        <div class="radio-list">
                                            <label class="radio-inline">
                                                <div class="radio" id="uniform-active">
                                                    <span class="checked">
                                                        <input id="active" name="status" type="radio" value="1" {% if form.status.value == 1 %} checked {% endif %} >
                                                    </span>Active
                                                </div>
                                            </label><br>
                                            <label class="radio-inline">
                                                <div class="radio" id="uniform-not_active">
                                                    <span>
                                                        <input id="not_active" name="status" type="radio" value="0" {% if form.status.value == 0 %} checked {% endif %}>
                                                    </span>In-Active
                                                </div>
                                            </label>
                                        </div>
                                    </div>
                                </div>
                                <div class="col col-sm-4">
                                    <div class="form-group mb-3">
                                        <label for="verified" class="bold">Is Default ?</label>
                                        <div class="radio-list">
                                            <label class="radio-inline">
                                                <div class="radio" id="uniform-verified">
                                                    <span class="checked">
                                                        <input id="verified" name="verified" type="radio" value="1" >
                                                    </span>Yes
                                                </div>
                                            </label><br>
                                            <label class="radio-inline">
                                                <div class="radio" id="uniform-not_verified">
                                                    <span>
                                                        <input id="not_verified" name="verified" type="radio" value="0">
                                                    </span>No
                                                </div>
                                            </label>
                                        </div>
                                    </div>
                                </div>
                            </div>
                            <button class="btn btn-large btn-primary mb-3 w-auto" type="submit">Update <i class="fa fa-arrow-circle-right" aria-hidden="true"></i></button> 
                            </form>
                        </div>
                    </div>
            </div>
            <!-- END PAGE MAIN CONTENT INNER -->
            
            
        </div>
    <!-- END CONTENT BODY --> 
    </div>

    {% block script %}
    <script>

        // JavaScript code to display selected image file in the preview
        const input = document.getElementById('image-upload');
               const preview = document.getElementById('image-preview');
             
               input.addEventListener('change', function(event) {
                 const file = this.files[0]; // Get the selected file
                 if (file) {
                   const reader = new FileReader(); // Initialize FileReader object
             
                   reader.onload = function(event) {
                     const img = new Image(); // Create new image element
                     img.onload = function() {
               const maxWidth = 200; // Max width for the image preview
               const maxHeight = 200; // Max height for the image preview
               let width = img.width;
               let height = img.height;
       
               // Calculate new dimensions while maintaining aspect ratio
               if (width > height) {
                 if (width > maxWidth) {
                   height *= maxWidth / width;
                   width = maxWidth;
                 }
               } else {
                 if (height > maxHeight) {
                   width *= maxHeight / height;
                   height = maxHeight;
                 }
               }
       
               // Set the image dimensions
               img.width = width;
               img.height = height;
       
               // Clear any previous preview
               preview.innerHTML = '';
               preview.appendChild(img); // Append the image to the preview div
             };
       
                     img.src = event.target.result; // Set the image source
             
                     // Clear any previous preview
                     preview.innerHTML = '';
                     preview.appendChild(img); // Append the image to the preview div
                   }
             
                   reader.readAsDataURL(file); // Convert file to data URL format
                 } else {
                   preview.innerHTML = ''; // Clear preview if no file selected
                 }
       
                 document.getElementById('confirmbtns').style.display='block';
                 document.getElementById('fileselector').style.display='none';
               });
       
    </script>
    {% endblock script %}
    
{% endblock %}
=================================================================================================================
4) URL make this view
 #------------------------------------- LANGUAGE_LEVEL URLs----------------------------------------------------
    path('languageleveladd/',views.LanguageLevelCreateView.as_view(),name="languageleveladd"),
    path('languagelevellist/',views.LanguageLevelListView.as_view(),name="languagelevellist"),
    path('languagelevelupdate/<int:pk>/',views.LanguageLevelUpdateView.as_view(),name="languagelevelupdate"),
    path('languageleveldelete/<int:pk>/',views.LanguageLevelDeleteView.as_view(),name="languageleveldelete"),

  ===========================================================================================================
7) 

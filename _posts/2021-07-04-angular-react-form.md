---
layout: course-angular
title: React Form  
slug : angular-react-from
category: laptrinhweb
tags: [angular]
summery: React Form   
image: /images/blog/angular.png
description : Sử dụng React Form trong dự án angular. Hướng dẫn cài đặt  React Form vào dự án Angular. Hướng dẫn các tạo một ứng dụng  React Form.
youtubeId: 
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các bạn,hôm nay anh sẽ hướng dẫn mọi người cách <b>React Form</b> là như thế nào?

# **1.React Form là gì**

Chúng ta sử dụng React Form để xây dựng cấu trúc của 1 form trong component class. Chúng ta sử dụng Form Groups , Form Controls và From Array để xây dựng lên một form.

# **2.Sử dụng Reactive From như thế nào**

Bước 1 : Chúng ta sử import ReactiveFormsModule vào NgModule

{% highlight javascript linenos %}

import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';
import { ReactiveFormsModule } from '@angular/forms';
 
import { AppRoutingModule } from './app-routing.module';
import { AppComponent } from './app.component';
 
@NgModule({
  declarations: [
    AppComponent
  ],
  imports: [
    BrowserModule,
    AppRoutingModule,
    ReactiveFormsModule
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }

{% endhighlight %} 

Bước 2 : Tạo Model cho From chúng ta sử dụng FormGroup, FormControl và Validator 

{% highlight javascript linenos %}

import { FormGroup, FormControl, Validators } from '@angular/forms'

{% endhighlight %} 

Chúng ta tạo FromGroup. FromGroup được sử dụng để tạo các form control. Form control là các input , button mà ta thấy trên giao diện form.

{% highlight javascript linenos %}

contactForm = new FormGroup({})

{% endhighlight %} 

Tiếp đến chúng ta tạo các form control

{% highlight javascript linenos %}

contactForm = new FormGroup({
  firstname: new FormControl(),
  lastname: new FormControl(),
  email: new FormControl(),
  gender: new FormControl(),
  isMarried: new FormControl(),
  country: new FormControl()
})

{% endhighlight %} 

Bước 3 : Chúng ta tạo form bên template html 


{% highlight javascript linenos %}

<form">
 
  <p>
    <label for="firstname">First Name </label>
    <input type="text" id="firstname" name="firstname">
  </p>
 
  <p>
    <label for="lastname">Last Name </label>
    <input type="text" id="lastname" name="lastname">
  </p>
 
  <p>
    <label for="email">Email </label>
    <input type="text" id="email" name="email">
  </p>
 
  <p>
    <label for="gender">Geneder </label>
    <input type="radio" value="male" id="gender" name="gender"> Male
    <input type="radio" value="female" id="gender" name="gender"> Female
  </p>
 
  <p>
    <label for="isMarried">Married </label>
    <input type="checkbox" id="isMarried" name="isMarried">
  </p>
 
  <p>
    <label for="country">country </label>
    <select id="country" name="country">
      <option [ngValue]="c.id" *ngFor="let c of countryList">
        {{c.name}}
      </option>
    </select>
  </p>
 
  <p>
    <button type="submit">Submit</button>
  </p>
 
</form>
{% endhighlight %} 

Bước 4 : Binding template html vào model form bên component class

{% highlight javascript linenos %}

<form [formGroup]="contactForm">

{% endhighlight %} 

Bước 5 : Binding các trường trong form vào FromControl models

{% highlight javascript linenos %}

<input type="text" id="firstname" name="firstname" formControlName="firstname">
<input type="text" id="lastname" name="lastname" formControlName="lastname">

{% endhighlight %} 


Bước 6 : Submit form, chúng ta sử dụng ngSubmit 

{% highlight javascript linenos %}

<form [formGroup]="contactForm" (ngSubmit)="onSubmit()">

{% endhighlight %} 

# **3 . Final Template html**

{% highlight javascript linenos %}

<form [formGroup]="contactForm" (ngSubmit)="onSubmit()">
 
  <p>
    <label for="firstname">First Name </label>
    <input type="text" id="firstname" name="firstname" formControlName="firstname">
  </p>
 
  <p>
    <label for="lastname">Last Name </label>
    <input type="text" id="lastname" name="lastname" formControlName="lastname">
  </p>
 
  <p>
    <label for="email">Email </label>
    <input type="text" id="email" name="email" formControlName="email">
  </p>
 
  <p>
    <label for="gender">Geneder </label>
    <input type="radio" value="male" id="gender" name="gender" formControlName="gender"> Male
    <input type="radio" value="female" id="gender" name="gender" formControlName="gender"> Female
  </p>
 
  <p>
    <label for="isMarried">Married </label>
    <input type="checkbox" id="isMarried" name="isMarried" formControlName="isMarried">
  </p>
 
  <p>
    <label for="country">country </label>
    <select id="country" name="country"  formControlName="country">
      <option [ngValue]="c.id" *ngFor="let c of countryList">
        {{c.name}}
      </option>
    </select>
  </p>
 
  <p>
    <button type="submit">Submit</button>
  </p>
 
</form>

{% endhighlight %} 

# **4. Sử dụng FormGroup**

Chúng ta sử dụng FormGroup để nhóm các control cùng với nhau. Ví dụ như ta có field là address (địa chỉ) trong địa chỉ có các thuộc tính như city, street, pincode. Thì ta có thể nhóm các thuộc tính đó lại trong Address như sau


{% highlight javascript linenos %}

contactForm = new FormGroup({
  firstname: new FormControl(),
  lastname: new FormControl(),
  email: new FormControl(),
  gender: new FormControl(),
  isMarried: new FormControl(),
  country: new FormControl(),
  address:new FormGroup({
    city: new FormControl(),
    street: new FormControl(),
    pincode:new FormControl()
  })
})
{% endhighlight %} 

- Chúng ta sử dụng trong template html như sau

{% highlight html linenos %}

<div formGroupName="address">
  
    <div class="form-group">
        <label for="city">City</label>
        <input type="text" class="form-control" name="city" formControlName="city" >
    </div>
 
    <div class="form-group">
        <label for="street">Street</label>
        <input type="text" class="form-control" name="street" formControlName="street" >
    </div>
 
    <div class="form-group">
        <label for="pincode">Pin Code</label>
        <input type="text" class="form-control" name="pincode" formControlName="pincode">
    </div>
 
  </div>

{% endhighlight %}

# **5. Sử dụng FormArray**

Ta có lớp component class sau app.component.ts

{% highlight html linenos %}

import { Component, ViewChild, ElementRef } from '@angular/core';
import { FormGroup, FormControl,FormArray, FormBuilder } from '@angular/forms'
 
 
@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent  {
  
  title = 'FormArray Example in Angular Reactive forms';
 
  skillsForm: FormGroup;
 
  constructor(private fb:FormBuilder) {
 
    this.skillsForm = this.fb.group({
      name: '',
      skills: this.fb.array([]) ,
    });
  
  }
 
  get skills() : FormArray {
    return this.skillsForm.get("skills") as FormArray
  }
 
  newSkill(): FormGroup {
    return this.fb.group({
      skill: '',
      exp: '',
    })
  }
 
  addSkills() {
    this.skills.push(this.newSkill());
  }
 
  removeSkill(i:number) {
    this.skills.removeAt(i);
  }
 
  onSubmit() {
    console.log(this.skillsForm.value);
  }
 
}
 
 
export class country {
  id: string;
  name: string;
 
  constructor(id: string, name: string) {
    this.id = id;
    this.name = name;
  }
}
{% endhighlight %}

Ta có lớp template html sau app.component.html

{% highlight html linenos %}

<form [formGroup]="skillsForm" (ngSubmit)="onSubmit()">
 
  <p>
    <label for="name">Name </label>
    <input type="text" id="name" name="name" formControlName="name">
  </p>
 
 
  Skills:
  <div formArrayName="skills">
    <div *ngFor="let skill of skills().controls; let i=index">
      <div [formGroupName]="i">
        {{i}}
        skill name :
        <input type="text" formControlName="skill">
        exp:
        <input type="text" formControlName="exp">
 
        <button (click)="removeSkill(i)">Remove</button>
      </div>
    </div>
  </div>
 
  <p>
    <button type="submit">Submit</button>
  </p>
 
</form>
 
 
<p>
  <button type="button" (click)="addSkills()">Add</button>
</p>
 

{% endhighlight %}

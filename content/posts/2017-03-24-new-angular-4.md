---
title: 'أهم الميزات الجديدة في إصدار أنغولار 4'
date: '2017-03-24'
slug: 'web-development/javascript/new-angular-4'
template: 'post'
categories:
  - أخبار
  - جافاسكريبت
tags:
  - angular
  - إطار العمل
thumbnail: '../thumbnails/angular.png'
---

أُعلِن مؤخرا عن الإصدار الجديد [لإطار العمل المعروف **أنغولار Angular**](http://www.tutomena.com/web-development/javascript/choose-angular/) الخاص بلغة البرمجة **جافاسكريبت**، والذي تقرر في وقت سابق إعطاؤه الرقم 4.

نسخة **أنغولار 4 Angular** الجديدة لم تأتي بتغييرات جذرية بطبيعة الحال، مثلما كان الوضع عند الإنتقال من الإصدار 1 إلى الإصدار 2، ولكنها جاءت بعدد من التحسينات والميزات الجديدة التي من شأنها زيادة سرعة وكفاءة تطبيقات الويب المدعومة من **إطار العمل أنغولار 4**.

## 1. إمكانية استخدام Else مع If في القوالب

في الإصدار **Angular 2** كنا نستطيع إضافة الوسم *ngIf لعنصر معين داخل القالب *Template* وإظهار هذا العنصر أو إخفائه بناءً على التعبير داخل الوسم `*ngIf` :

```html
<p *ngIf="isLoggedIn">You are logged in as</p>
```

في هذا المثال نقوم بإظهار هذا النص إذا كان المستخدم مُعَرَّفًا (Authenticated)، ولكن ماذا لو لم يكن الحال كذلك ؟ في الماضي كنا نضيف وسم \*ngIf  آخر للعنصر الثاني الذي نريد إظهاره في الحالة المعاكسة :

```html
<p *ngIf="isLoggedIn">You are logged in</p>
<p *ngIf="!isLoggedIn">You are not logged in</p>
```

ولكن مع الوسم الجديد Else ، الأمر بات أبسط :

```html
<element *ngIf="[condition expression]; else [else template]"> </element>

<ng-template #hidden>
  <p>You are not logged in</p>
</ng-template>
<p *ngIf="shown; else hidden">
  You are logged in!
</p>
```

## 2. وحدة الأنيميشن Animation Module

الأنيمشن كانت موجودة في إصدار أنغولار 2 ولكنها كانت مدمجة في نواة البرنامج `@angular/core` وكان يتم استدعاؤها على هذا النحو :

```js
import {
Component,
OnInit
// Animation modules
animate,
state,
style,
transition,
trigger } from '@angular/core'
```

ولكن مع إصدار **أنغولار 4**، تقرر تخصيص وحدة خاصة منفصلة للأنيميشن فيتم استدعاؤها فقط في حال احتجنا إليها :

```js
import { Component, OnInit } from '@angular/core';

//Animations modules
import {
  animate,
  state,
  style,
  transition,
  trigger,
} from '@angular/animations';
```

## 3. Angular Universal

لطالما كان السيو SEO ووصول محركات البحث لمحتوى صفحاتنا أكبر المشاكل التي واجهت ولا تزال تواجه إطارات عمل جافاسكريبت المعروفة مثل **أنغولار**، [React.js](/web-development/javascript/react-javascript-library/)، **Vue.js** وغيرها. فالمحتوى (كود HTML) يتم توليده داخل المتصفح وليس من الخادم كما هو شائع.

**Angular Universal** هو أحد المشاريع التي جاءت بهدف إيجاد حل لهذه المعضلة، دوره هو توليد محتوى الصفحة كاملا داخل الخادم قبل إرسالها للمتصفح. هذا المشروع كان مدعوما من طرف عدد من المطورين من خارج الفريق الرسمي لأنغولار، ولكن مع قدوم **أنغولار 4** قرر القائمون على هذا الإطار ضم [Angular Universal](https://universal.angular.io/) بشكل رسمي، أي أنه أصبح الآن جزءً من **إطار العمل Angular 4**.

## 4. الشيفرة النهائية أصبحت أخف

قام مطورو أنغولار 4 بمجهود كبير لتحسين طريقة توليد كود الجافاسكريبت النهائي للمشروع، فنجحوا في جعله أخف ب 60% تقريبا عما كان عليه الحال من قبل، وستلاحظ الفرق بنفسك كلما كان حجم المشروع أكبر، حيث أكد عدد من المطورين أن الإنتقال من الإصدار 2 إلى الإصدار 4 خفض وزن ملفات المشروع النهائية بمئات الكيلو بايت.

## 5. أنغولار 4 متوافق مع تايب سكريبت 2.1 و 2.2

إطار العمل أنغولار 4 بات متوافقا مع إصدارات **Typescript** الأخيرة، هذا سيمكن المطورين من الإستفادة من الميزات الجديدة لهذا الأخير في مشاريعهم.

## 6. الخريطة المصدرية للقوالب Source maps for templates

هذه إضافة رائعة وعملية بشكل كبير، فعند التنفيذ قد يكون هناك خطأ في أحد القوالب داخل الصفحة، ودور هذه **الخرائط المصدرية Source maps** هو إيجاد مصدر الخطأ بشكل محدد، فكما نعلم جميعا، الشيفرة النهائية التي يتم توليدها لا تمكن من تتبع مصدر الخطأ بشكل دقيق.

### خاتمة

من الواضح أن مطوري إطار العمل أنغولار يعملون بشكل جاد لإبقاء هذا المشروع على قمة إطارات عمل الجافاسكريبت خاصة إذا علمنا أنهم [ينوون إصدار نسخة كبيرة كل 6 أشهر](https://github.com/angular/angular/blob/master/docs/RELEASE_SCHEDULE.md). ضم مشروع **Angular Universal** خطوة ممتازة لحل إشكالية السيو _SEO_ التي كانت دائما أحد العيوب الكبيرة لأنغولار وأخواتها.

أدعوكم، عشاق **Angular**، لتجربة هذا الإصدار وإبداء ملاحظاتم وآرائكم في صندوق التعليقات أسفله :)

---

### المراجع:

- [https://scotch.io/tutorials/5-features-to-watch-out-for-in-angular-4](https://scotch.io/tutorials/5-features-to-watch-out-for-in-angular-4)
- [https://www.nextinpact.com/news/103797-angular-4-0-disponible-objectif-reduire-poids-applications-web.htm](https://www.nextinpact.com/news/103797-angular-4-0-disponible-objectif-reduire-poids-applications-web.htm)
- [http://angularjs.blogspot.com/2017/03/angular-400-now-available.html](http://angularjs.blogspot.com/2017/03/angular-400-now-available.html)

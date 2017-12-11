---
title: "Управление прослушивателями событий | Документы Майкрософт"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 87717f5d-b0c6-4c8d-a293-476002b7bfcf
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6a97c579716b9964b8dfb93db419e9a70160d33a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="managing-event-listeners"></a>Управление прослушивателями событий
Если время существования элемента DOM или объекта отличается от времени существования связанного с ним прослушивателя событий, может потребоваться использовать метод [removeEventListener](http://msdn.microsoft.com/library/ie/ff975250\(v=vs.85\).aspx), чтобы избежать утечки памяти.  
  
## <a name="event-listeners-and-object-scope"></a>Прослушиватели событий и область объекта  
 В следующем примере приведен код, который может вызвать утечку памяти при вызове функции `dataObjFactory()`. В этом коде прослушиватель событий регистрируется для объекта данных каждый раз при создании нового объекта данных. Чтобы сделать текущий объект данных доступным в прослушивателе событий `dataReady()`, в `addEventListener` используется [метод bind (Function)](../../javascript/reference/bind-method-function-javascript.md).  
  
```JavaScript  
 var data;  
 var dataObj;  
  
 var dataReadyEvent = document.createEvent("Event");  
 dataReadyEvent.initEvent("dataReady", true, false);  
  
 function DataObject() {  
  
     this.name = "Data Object";  
     this.data = function () {  
         return data;  
     }  
     this.onDataCompleted = dataReady;  
     // this.handlerRef = this.onDataCompleted.bind(this);  
  
     // document.addEventListener('dataReady', this.handlerRef);  
     document.addEventListener('dataReady', this.onDataCompleted.bind(this));  
 }  
  
 // Runs when the data is available.  
 function dataReady() {  
     if (console && console.log) {  
         console.log("object value: " + this.name);  
         console.log("object value: " + this.data());  
     }  
 }  
  
setTimeout(function () {  
    // Generate data after a timeout period.  
    data = [0, 1, 2, 3];  
    document.dispatchEvent(dataReadyEvent);  
}, 10000);  
  
function dataObjFactory() {  
     for (var x = 0; x < 100; x++) {  
         if (dataObj) {  
             // The following line of code has no effect.  
             document.removeEventListener('dataReady', dataObj.onDataCompleted);  
             dataObj = null;  
         }  
         dataObj = new DataObject();  
     }  
 }  
  
 dataObjFactory();  
```  
  
 Прослушиватель для каждого объекта данных регистрируется с объектом `document`, срок существования которого отличается от объектов данных. Создание зарегистрированного прослушивателя событий для каждого объекта данных предотвращает его уничтожение сборщиком мусора, пока объект `document` остается в области. (В некоторых современных шаблонах разработки JavaScript объекты document остаются в области в течение срока существования веб-приложения.) Во избежание утечки памяти метод `removeEventListener` вызывается в функции `dataObjFactory`. Однако происходит сбой этого кода, так как метод `removeEventListener` не был вызван в привязанной версии обработчика событий, возвращенного функцией `bind`.  
  
 Чтобы внести исправления в этот код и сделать объекты данных доступными для сборки мусора, необходимо сначала сохранить ссылку на привязанную версию обработчика событий, как показано в этом примере кода, а затем передать сохраненную ссылку в `addEventListener`. Ниже приведен исправленный код для объекта `DataObject`:  
  
```JavaScript  
function DataObject() {  
  
    this.name = "Data Object";  
    this.data = function () {  
        return data;  
    }  
    this.onDataCompleted = dataReady;  
    this.handlerRef = this.onDataCompleted.bind(this);  
  
    document.addEventListener('dataReady', this.handlerRef);  
    // document.addEventListener('dataReady', this.onDataCompleted.bind(this));  
}  
  
```  
  
 Наконец, необходимо вызвать метод `removeEventListener` для сохраненной ссылки (`handlerRef`) привязанной функции. Ниже приведен исправленный код для объекта `dataObjFactory`:  
  
```JavaScript  
function dataObjFactory() {  
     for (var x = 0; x < 100; x++) {  
         if (dataObj) {  
             document.removeEventListener('dataReady', dataObj.handlerRef);  
         }  
         dataObj = new DataObject();  
     }  
 }  
  
```  
  
 Теперь вызовы к `removeEventListener` работают и ненужные объекты данных могут уничтожаться сборщиком мусора, даже если объект `document` остается в области.
---
title: "IRemoteDebugApplication::CreateInstanceAtApplication | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplication.CreateInstanceAtApplication
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplication::CreateInstanceAtApplication"
ms.assetid: d669ec80-2182-400d-87cc-7c1753315e5c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplication::CreateInstanceAtApplication
Разрешает создание объектов в обработке приложения кодом, вне процесса.  
  
## Синтаксис  
  
```  
HRESULT CreateInstanceAtApplication(  
   REFCLSID    rclsid,  
   IUnknown*   pUnkOuter,  
   DWORD       dwClsContext,  
   REFIID      riid,  
   IUnknown**  ppvObject  
);  
```  
  
#### Параметры  
 `rclsid`  
 \[in\] идентификатор класса \(CLSID\) объекта, который необходимо создать.  
  
 `pUnkOuter`  
 \[in\] если `NULL`, объект не создавать как часть пользователем агрегате.  В противном случае \- значение `pUnkOuter` указатель на интерфейс объекта `IUnknown` aggregate \(управление `IUnknown`\).  
  
 `dwClsContext`  
 \[in\] контекст для выполнения исполняемого кода.  Значения берутся из перечисления `CLSCTX`.  
  
 `riid`  
 \[in\] идентификатор интерфейса, используемый для взаимодействия с объектом.  
  
 `ppvObject`  
 \[out\] Адрес переменной указателя, получающей указатель интерфейса, запрашиваемый в `riid`.  При удачном возвращении \- \*`ppvObject` содержит указатель интерфейса.  В случае сбоя, \*`ppvObject` содержит `NULL`.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Делегаты этого метода в `CoCreateInstance`.  
  
## См. также  
 [Интерфейс IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md)
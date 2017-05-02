---
title: "IApplicationDebugger::CreateInstanceAtDebugger | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IApplicationDebugger.CreateInstanceAtDebugger
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IApplicationDebugger::CreateInstanceAtDebugger"
ms.assetid: 6763afac-c86a-4e88-9580-77108fb242fb
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IApplicationDebugger::CreateInstanceAtDebugger
Разрешает создание объектов в процессе отладчика кодом, вне процесса в отладчике.  
  
> [!IMPORTANT]
>  Этот метод не должен быть реализован, поскольку он позволяет ненадежный код для создания произвольных объектов в доверенном потоке отладчика.  
  
## Синтаксис  
  
```  
HRESULT CreateInstanceAtDebugger(  
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
  
 Метод в настоящее время не реализуется.  
  
## См. также  
 [Интерфейс IApplicationDebugger](../../winscript/reference/iapplicationdebugger-interface.md)
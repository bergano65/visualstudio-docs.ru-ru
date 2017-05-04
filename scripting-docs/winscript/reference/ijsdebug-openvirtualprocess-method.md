---
title: "Метод IJsDebug::OpenVirtualProcess | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJSDebug.OpenVirtualProcess
apilocation: jscript9diag.dll
ms.assetid: 5612bf1b-a4e3-4eaf-ac5e-c2e1f147c395
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Метод IJsDebug::OpenVirtualProcess
Фабричный метод, используемый для создания нового объекта виртуального процесса.  
  
## Синтаксис  
  
```  
 HRESULT OpenVirtualProcess(  
   DWORD processId,  
   UINT64 runtimeJsBaseAddress,  
   IJsDebugDataTarget *pDataTarget,  
   IJsDebugProcess **ppProcess  
);  
```  
  
#### Параметры  
 `processId`  
 \[in\] ИД процесса для прикрепления отладчика  
  
 `runtimeJsBaseAddress`  
 \[in\] Базовый адрес, по которому среда выполнения JavaScript загружена в целевой процесс.  
  
 `pDataTarget`  
 \[in\] Интерфейс отладчика для запроса состояния процесса.  
  
 `ppProcess`  
 \[out\] Новый объект процесса отладки  
  
## Возвращаемое значение  
  
## Заметки  
 Возвращает E\_JsDEBUG\_MISMATCHED\_RUNTIME при Jscript9diag и Jscript9 не совпадают.  
  
## Требования  
 **Заголовок:** jscript9diag.h  
  
## См. также  
 [Интерфейс IJsDebug](../../winscript/reference/ijsdebug-interface.md)
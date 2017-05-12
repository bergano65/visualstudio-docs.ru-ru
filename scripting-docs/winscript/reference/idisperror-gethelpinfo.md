---
title: "IDispError::GetHelpInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispError.GetHelpInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDispError::GetHelpInfo"
ms.assetid: a146df13-eda4-4e56-8bf0-cf9886a2150f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispError::GetHelpInfo
Возвращает путь к файлу Справки и контекстного идентификатора разделы с описанием ошибки, если возможно.  
  
## Синтаксис  
  
```  
HRESULT GetHelpInfo(  
   BSTR*  pbstrFileName,  
   DWORD*  pdwContext  
);  
```  
  
#### Параметры  
 `pbstrFileName`  
 \[out\] строка, содержащая полный путь к файлу Справки.  Если файл Справки или ошибка возникает, то возвращаемое значение равно null.  
  
 `pdwContext`  
 \[out\] идентификатор контекста Справки для ошибки.  Если файл Справки \(если `pbstrFileName` значение null\), то этот параметр не имеет смысла.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_FAIL`|Произошла ошибка поставщик\- в XML\-структуру.|  
|`E_INVALIDARG`|`pbstrFileName` или `pdwContext` были равны null.|  
|`E_OUTOFMEMORY`|Поставщик не смог выделить достаточно памяти, в которой требуется возвратить путь к файлу Справки.|  
  
## Заметки  
 Этот метод возвращает путь к файлу Справки и контекстного идентификатора разделы с описанием ошибки, если возможно.  
  
> [!NOTE]
>  Этот метод не реализован.  
  
## См. также  
 [Интерфейс IDispError](../../winscript/reference/idisperror-interface.md)
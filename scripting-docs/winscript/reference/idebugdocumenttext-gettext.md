---
title: "IDebugDocumentText::GetText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentText.GetText
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentText::GetText"
ms.assetid: 3c940a30-6c0f-4deb-aa4d-21a0bdef8461
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentText::GetText
Извлекает символы и атрибуты знака, связанные с диапазоном позиции символа.  
  
## Синтаксис  
  
```  
HRESULT GetText(  
   ULONG              cCharacterPosition,  
   WCHAR*             pcharText,  
   SOURCE_TEXT_ATTR*  pstaTextAttr,  
   ULONG*             pcNumChars,  
   ULONG              cMaxChars  
);  
```  
  
#### Параметры  
 `cCharacterPosition`  
 \[in\] начальное положение диапазона позиции символа.  
  
 `pcharText`  
 \[in, out\] текстовый буфер символов, а.  Буфер должен быть достаточным для хранения символов `cMaxChars`.  Если этот параметр равен null, метод не возвращает символы.  
  
 `pstaTextAttr`  
 \[in, out\] буфер атрибута символа, а.  Буфер должен быть достаточным для хранения символов `cMaxChars`.  Если этот параметр равен null, метод не возвращает атрибуты.  
  
 `pcNumChars`  
 \[in, out\] количество символов возвращенных\/атрибутов.  Этот параметр необходимо устанавливать равным нулю до вызова этого метода.  
  
 `cMaxChars`  
 \[in\] количество символов в диапазоне позиции символа.  Также определяет максимальное количество знаков для возврата.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Этот метод извлекает атрибуты символов или знаков, связанные с позиции символа в диапазоне.  Диапазон позиции символа определено позиции символа и несколькими символами.  
  
## См. также  
 [Интерфейс IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md)   
 [Перечисление SOURCE\_TEXT\_ATTR](../../winscript/reference/source-text-attr-enumeration.md)
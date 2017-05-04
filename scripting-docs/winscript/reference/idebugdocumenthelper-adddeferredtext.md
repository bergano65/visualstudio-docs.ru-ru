---
title: "IDebugDocumentHelper::AddDeferredText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.AddDeferredText
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::AddDeferredText"
ms.assetid: 9463cfb0-76cc-45ee-b32c-f37dce2b2e0e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::AddDeferredText
Уведомляет вспомогательная подпрограмма, что заданный текст доступно, но не содержатся символы.  
  
## Синтаксис  
  
```  
HRESULT AddDeferredText(  
   ULONG  cChars,  
   DWORD  dwTextStartCookie  
);  
```  
  
#### Параметры  
 `cChars`  
 \[in\] количество символов \(юникод\) для добавления.  
  
 `dwTextStartCookie`  
 \[in\] базовая приложение\- указанный файл cookie, представляющее начальную позицию текста.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_FAIL`|Сбой метода.|  
  
## Заметки  
 Этот метод позволяет узлу отложить защита символы, чтобы добавить до тех пор, пока они не будут необходимы, пока что вспомогательный метод для создания точных уведомления и данные о размере.  Параметр `dwTextStartCookie` файл cookie, определяемый основным приложением, которое представляет начальную позицию текста.  Последующие вызовы `IDebugDocumentText::GetText` должны предоставить этот файл cookie.  Например, в основном приложении, которое представляет текст в двухбайтовой кодировке, файл " cookie " может быть возмещенным байтом.  
  
 Ожидается один вызов `IDebugDocumentText::GetText` может получить символы из нескольких вызовов `AddDeferredText`.  Вспомогательные классы могут также просить тот же диапазон символов отложенную несколько раз.  
  
> [!NOTE]
>  Вызовы `AddDeferredText` не должны быть смешаны с вызовами к `AddUnicodeText` или `AddDBCSText`.  Если это происходит, `E_FAIL` возвращается.  
  
## См. также  
 [Интерфейс IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)   
 [IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)
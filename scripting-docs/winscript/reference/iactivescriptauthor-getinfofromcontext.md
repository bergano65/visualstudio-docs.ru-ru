---
title: "IActiveScriptAuthor::GetInfoFromContext | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.GetInfoFromContext
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::GetInfoFromContext"
ms.assetid: 9891b095-6eb5-4473-87c0-c2e5cd2afc1a
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# IActiveScriptAuthor::GetInfoFromContext
Извлечения сведений о типе и положения привязки для заданного символа в блоке кода.  Это предоставляет сведения для членов IntelliSense, глобальных списков и советы по параметра.  
  
## Синтаксис  
  
```  
HRESULT GetInfoFromContext(  
   LPCOLESTR  pszCode,  
   ULONG      cchCode,  
   ULONG      ichCurrentPosition,  
   DWORD      dwListTypesRequested,  
   DWORD      *pdwListTypesProvided,  
   ULONG      *pichListAnchorPosition,  
   ULONG      *pichFuncAnchorPosition,  
   MEMBERID   *pmemid,  
   LONG       *piCurrentParameter,  
   IUnknown   **ppunk  
);  
```  
  
#### Параметры  
 `pszCode`  
 \[in\] адрес строки блока кода, используемой для создания сведений результатов.  
  
 `cchCode`  
 \[in\] длина блока кода.  
  
 `ichCurrentPosition`  
 \[in\] позиция символа относительно начала блока.  
  
 `dwListTypesRequested`  
 \[in\] список типа.  Может быть сочетанием следующих значений:  
  
|Константа|Значение|Описание|  
|---------------|--------------|--------------|  
|SCRIPT\_CMPL\_NOLIST|0x0000|Нет списка.|  
|SCRIPT\_CMPL\_MEMBERLIST|0x0001|Список членов.|  
|SCRIPT\_CMPL\_ENUMLIST|0x0002|Список Перечисления.|  
|SCRIPT\_CMPL\_PARAMLIST|0x0004|Список параметров метода вызова.|  
|SCRIPT\_CMPL\_GLOBALLIST|0x0008|Глобальный список.|  
  
 Тип обрабатывается как SCRIPT\_CMPL\_GLOBALLIST по умолчанию элемент завершения, который может быть объединяется с помощью оператора " ИЛИ с другими элементами завершения.  Скрипт создание обработчика сначала пытается заполнить сведения о типе для других элементов списка завершения.  Если происходит сбой, то обработчик заполняет для SCRIPT\_CMPL\_GLOBALLIST.  
  
 `pdwListTypesProvided`  
 \[out\] предоставленный тип списка.  
  
 `pichListAnchorPosition`  
 \[out\] начальный индекс контекста, содержащий текущую позицию.  Начальный индекс относительно начала блока.  
  
 Это заполнитьо только при `dwListTypesRequested` включает SCRIPT\_CMPL\_MEMBERLIST, SCRIPT\_CMPL\_ENUMLIST или SCRIPT\_CMPL\_GLOBALLIST.  Для других типов списков, не найдена, результат является неопределенным.  
  
 `pichFuncAnchorPosition`  
 \[out\] начальный индекс вызова функции, содержащий текущую позицию.  Начальный индекс относительно начала блока.  
  
 Это заполнитьо, только если контекст, содержащий текущую позицию вызов функции и при `dwListTypesRequested` включает SCRIPT\_CMPL\_PARAMLIST.  В противном случае результат является неопределенным.  
  
 `pmemid`  
 \[out\] MEMBERID функции, как определяется типом в параметре `IProvideMultipleClassInfo``ppunk` ожидания.  
  
 Это заполнитьо только при `dwListTypesRequested` включает SCRIPT\_CMPL\_PARAMLIST.  
  
 `piCurrentParameter`  
 \[out\] индекс параметра, содержащий текущую позицию.  Если текущая позиция на имени функции, то возвращается значение \-1.  
  
 Значение `piCurrentParameter` заполнитьо только при `dwListTypesRequested` включает SCRIPT\_CMPL\_PARAMLIST.  
  
 `ppunk`  
 Сведения о типе, приведенную в форме объекта `IProvideMultipleClassInfo`.  
  
## Возвращаемое значение  
 Объект `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
  
## См. также  
 <xref:Microsoft.VisualStudio.OLE.Interop.IProvideMultipleClassInfo>   
 [Интерфейс IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)
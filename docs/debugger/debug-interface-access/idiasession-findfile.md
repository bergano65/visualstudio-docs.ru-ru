---
title: "IDiaSession::findFile | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaSession::findFile - метод"
ms.assetid: a215dc21-b316-40d7-9923-55bfa014976b
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSession::findFile
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Извлекает исходные файлы compiland и именем.  
  
## Синтаксис  
  
```cpp#  
HRESULT findFile (   
   IDiaSymbol*           pCompiland,  
   LPCOLESTR             name,  
   DWORD                 option,  
   IDiaEnumSourceFiles** ppResult  
);  
```  
  
#### Параметры  
 `pCompiland`  
 \[in\] объект [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md), представляющий compiland, используемый в качестве контекста для поиска.  Установите этот параметр в `NULL` чтобы найти исходные файлы во всех compilands.  
  
 `name`  
 \[in\] определяет имя исходного файла, который необходимо извлечь.  Установите этот параметр в `NULL` для всех исходных файлов для извлечения.  
  
 `option`  
 \[in\] определяет параметры сравнения, применяемые для именования поиск.  Значения из перечисления [Перечисление NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md) можно использовать по отдельности или в сочетании.  
  
 `ppResult`  
 \[out\] возвращает объект [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md), содержащий список извлеченных исходных файлов.  
  
## Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## Пример  
  
```cpp#  
IDiaEnumSourceFiles* pEnum;  
pSession->findFile( NULL, L"sourcefile.cpp", nsFNameExt, &pEnum );  
```  
  
## См. также  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Перечисление NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md)
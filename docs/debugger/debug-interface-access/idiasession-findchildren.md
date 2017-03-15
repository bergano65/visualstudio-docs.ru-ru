---
title: "IDiaSession::findChildren | Microsoft Docs"
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
  - "IDiaSession::findChildren - метод"
ms.assetid: 5d19046f-f668-4aa9-8788-95cda9a98997
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaSession::findChildren
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Извлекает все дочерние элементы указанного родительского идентификатора, соответствующие имени и типа символа.  
  
## Синтаксис  
  
```cpp#  
HRESULT findChildren (   
   IDiaSymbol*       parent,  
   SymTagEnum        symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### Параметры  
 `parent`  
 \[in\] [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) объект, представляющий родительский элемент.  Если этот родительский символ функция, модуля или блока, то его возвращаемые в лексических дочерние элементы `ppResult`.  Если родительский символ тип, его дочерние элементы класса возвращаются.  Если этот параметр `NULL`после этого  `symtag` должен быть присвоено  `SymTagExe` OR  `SymTagNull`, который получает глобальную область \(EXE\-файл\).  
  
 `symtag`  
 \[in\] определяет тега символов дочерних элементов, которые необходимо извлечь.  Значения берутся из [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) перечисление.  Значение `SymTagNull` извлечь все дочерние элементы.  
  
 `name`  
 \[in\] определяет имя дочерних элементов, которые необходимо извлечь.  Значение `NULL` для всех дочерних элементов, которые необходимо извлечь.  
  
 `compareFlags`  
 \[in\] определяет параметры сравнения, применяемые для именования совпадать.  Значения [Перечисление NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md) перечисление можно использовать по отдельности или в сочетании.  
  
 `ppResult`  
 \[out\] возвращает [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) объект, содержащий список полученных символов дочернего элемента.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Пример  
 В следующем примере показано, как найти локальные переменные, функции `pFunc` это имя сопоставления  `szVarName`.  
  
```cpp#  
IDiaEnumSymbols* pEnum;  
pSession->findChildren( pFunc, SymTagData, szVarName, nsCaseSensitive, &pEnum );  
```  
  
## См. также  
 [Обзор](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Перечисление NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md)   
 [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)
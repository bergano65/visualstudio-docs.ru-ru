---
title: "IDiaSession::findChildren | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findChildren method
ms.assetid: 5d19046f-f668-4aa9-8788-95cda9a98997
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 0cae2dd492fd11ff4a5d707ba95c571711358358
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idiasessionfindchildren"></a>IDiaSession::findChildren
Извлекает все дочерние элементы идентификатора указанного родительского объекта, соответствующие типу наименование и символ.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT findChildren (   
   IDiaSymbol*       parent,  
   SymTagEnum        symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `parent`  
 [in] [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) объект, представляющий родительский объект. Если этот символ родительской функцией, модулем или блоком, то его дочерние лексические элементы возвращаются в `ppResult`. Если родительский символ имеет тип, его дочерних элементов класса возвращаются. Если этот параметр имеет `NULL`, затем `symtag` должно быть присвоено `SymTagExe` или `SymTagNull`, который возвращает глобальной области (файл .exe).  
  
 `symtag`  
 [in] Указывает тег символа дочерних элементов, которые требуется получить. Значения берутся из [SymTagEnum-перечисление](../../debugger/debug-interface-access/symtagenum.md) перечисления. Значение `SymTagNull` для получения всех дочерних элементов.  
  
 `name`  
 [in] Указывает имя дочерние элементы, которые требуется получить. Значение `NULL` для всех дочерних требуется получить.  
  
 `compareFlags`  
 [in] Задает параметры сравнения, применяется для сопоставления имени. Значения из [NameSearchOptions-перечисление](../../debugger/debug-interface-access/namesearchoptions.md) перечисления может использоваться отдельно или в сочетании.  
  
 `ppResult`  
 [out] Возвращает [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) извлечь объект, содержащий список дочерних символов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как для поиска локальных переменных функции `pFunc` , имя для поиска `szVarName`.  
  
```C++  
IDiaEnumSymbols* pEnum;  
pSession->findChildren( pFunc, SymTagData, szVarName, nsCaseSensitive, &pEnum );  
```  
  
## <a name="see-also"></a>См. также  
 [Обзор](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Перечисление NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md)   
 [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)
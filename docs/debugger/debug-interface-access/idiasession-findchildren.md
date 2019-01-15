---
title: IDiaSession::findChildren | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findChildren method
ms.assetid: 5d19046f-f668-4aa9-8788-95cda9a98997
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3d2e0db2ec3f1f8f50dce061900ac086deca7777
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53916286"
---
# <a name="idiasessionfindchildren"></a>IDiaSession::findChildren
Получает все дочерние элементы идентификатора указанного родительского элемента, которые соответствуют типу имя и символов.  
  
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
 [in] [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) объект, представляющий родительский объект. Если этот символ родительской функции, модуля или блока, то дочерние лексические возвращаются в `ppResult`. Если родительский символ относится к типу, его дочерних элементов класса возвращаются. Если этот параметр имеет `NULL`, затем `symtag` должно быть присвоено `SymTagExe` или `SymTagNull`, который возвращает глобальной области (файл .exe).  
  
 `symtag`  
 [in] Указывает тег символа дочерних элементов, которые требуется получить. Значения берутся из [перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) перечисления. Значение `SymTagNull` для получения всех дочерних элементов.  
  
 `name`  
 [in] Задает имя используемого дочерние элементы должны быть получены. Значение `NULL` для всех дочерних элементов, требуется получить.  
  
 `compareFlags`  
 [in] Задает параметры сравнения, который применяется к соответствующим именем. Значения из [перечисление NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md) перечисления можно использовать отдельно или в сочетании.  
  
 `ppResult`  
 [out] Возвращает [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) извлечь объект, содержащий список дочерних символов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как для поиска локальных переменных функции `pFunc` , имя для поиска `szVarName`.  
  
```C++  
IDiaEnumSymbols* pEnum;  
pSession->findChildren( pFunc, SymTagData, szVarName, nsCaseSensitive, &pEnum );  
```  
  
## <a name="see-also"></a>См. также раздел  
 [Обзор](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Перечисление NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md)   
 [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)
---
title: IDiaSession::findChildren | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findChildren method
ms.assetid: 5d19046f-f668-4aa9-8788-95cda9a98997
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cf274bb0f572da11a9aa43248da7eaa72a2e73c3
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58980437"
---
# <a name="idiasessionfindchildren"></a>IDiaSession::findChildren
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Получает все дочерние элементы идентификатора указанного родительского элемента, которые соответствуют типу имя и символов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
  
```cpp#  
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

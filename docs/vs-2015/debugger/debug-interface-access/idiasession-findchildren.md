---
title: 'IDiaSession:: Финдчилдрен | Документация Майкрософт'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150421"
---
# <a name="idiasessionfindchildren"></a>IDiaSession::findChildren
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Извлекает все дочерние элементы указанного родительского идентификатора, соответствующие имени и типу символа.  
  
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
 окне Объект [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , представляющий родительский элемент. Если этот родительский символ является функцией, модулем или блоком, то его лексические потомки возвращаются в `ppResult` . Если родительский символ является типом, возвращаются его дочерние элементы класса. Если этот параметр имеет `NULL` значение, то `symtag` для него должен быть задан `SymTagExe` или `SymTagNull` , который возвращает глобальную область (exe-файл).  
  
 `symtag`  
 окне Указывает тег символа для извлекаемых дочерних элементов. Значения берутся из перечисления [перечисления симтаженум](../../debugger/debug-interface-access/symtagenum.md) . Задайте для значение, `SymTagNull` чтобы получить все дочерние элементы.  
  
 `name`  
 окне Указывает имя извлекаемых дочерних элементов. Задайте значение, чтобы `NULL` получить все дочерние элементы.  
  
 `compareFlags`  
 окне Задает параметры сравнения, применяемые к соответствию имен. Значения из перечисления [перечисления намесеарчоптионс](../../debugger/debug-interface-access/namesearchoptions.md) можно использовать отдельно или в сочетании.  
  
 `ppResult`  
 заполняет Возвращает объект [идиаенумсимболс](../../debugger/debug-interface-access/idiaenumsymbols.md) , содержащий список полученных дочерних символов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как найти локальные переменные функции `pFunc` , соответствующие имени `szVarName` .  
  
```cpp#  
IDiaEnumSymbols* pEnum;  
pSession->findChildren( pFunc, SymTagData, szVarName, nsCaseSensitive, &pEnum );  
```  
  
## <a name="see-also"></a>См. также:  
 [Средств](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [идиаенумсимболс](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Перечисление Намесеарчоптионс](../../debugger/debug-interface-access/namesearchoptions.md)   
 [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)

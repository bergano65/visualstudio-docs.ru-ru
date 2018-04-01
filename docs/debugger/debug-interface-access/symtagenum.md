---
title: SymTagEnum | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- SymTagEnum enumeration
ms.assetid: 528a50cf-e13d-46ec-a98c-323d5d047de9
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 9165059991e4b961fc995b96a0c285f28a1587b4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="symtagenum"></a>SymTagEnum
Указывает тип символа.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
enum SymTagEnum {   
   SymTagNull,  
   SymTagExe,  
   SymTagCompiland,  
   SymTagCompilandDetails,  
   SymTagCompilandEnv,  
   SymTagFunction,  
   SymTagBlock,  
   SymTagData,  
   SymTagAnnotation,  
   SymTagLabel,  
   SymTagPublicSymbol,  
   SymTagUDT,  
   SymTagEnum,  
   SymTagFunctionType,  
   SymTagPointerType,  
   SymTagArrayType,   
   SymTagBaseType,   
   SymTagTypedef,   
   SymTagBaseClass,  
   SymTagFriend,  
   SymTagFunctionArgType,   
   SymTagFuncDebugStart,   
   SymTagFuncDebugEnd,  
   SymTagUsingNamespace,   
   SymTagVTableShape,  
   SymTagVTable,  
   SymTagCustom,  
   SymTagThunk,  
   SymTagCustomType,  
   SymTagManagedType,  
   SymTagDimension,  
   SymTagCallSite,  
   SymTagInlineSite,  
   SymTagBaseInterface,  
   SymTagVectorType,  
   SymTagMatrixType,  
   SymTagHLSLType  
};  
```  
  
## <a name="elements"></a>Элементы  
 `SymTagNull`  
 Указывает, что символ не имеет типа.  
  
 `SymTagExe`  
 Указывает, что символ представляет собой файл .exe. Имеется только один `SymTagExe` символ в хранилище символов. Он служит в качестве глобальной области и не имеет лексическую родительского.  
  
 `SymTagCompiland`  
 Указывает символ компилируемого объекта для каждого компонента компилируемого объекта в хранилище символов. Для собственных приложений `SymTagCompiland` символы соответствуют объектных файлов, связанных в образе. Для некоторых видов изображений промежуточного языка Майкрософт (MSIL) имеется один компилируемого объекта каждого класса.  
  
 `SymTagCompilandDetails`  
 Указывает, что символ содержит дополнительные атрибуты объекта компиляции. Для получения этих свойств может потребоваться загрузка символов компилируемого объекта.  
  
 `SymTagCompilandEnv`  
 Указывает символ определен для компилируемого объекта строки.  
  
 `SymTagFunction`  
 Указывает, что символ является функцией.  
  
 `SymTagBlock`  
 Указывает, что символ вложенного блока.  
  
 `SymTagData`  
 Указывает, что символ данных.  
  
 `SymTagAnnotation`  
 Указывает символ для аннотации кода. Дочерние элементы этого символа представляют собой постоянные данные строки (`SymTagData`, `LocIsConstant`, `DataIsConstant`). Большинство клиентов игнорировать этот символ.  
  
 `SymTagLabel`  
 Указывает символ метки.  
  
 `SymTagPublicSymbol`  
 Указывает, что символ открытых символов. Для собственных приложений этот символ используется при связывании изображения внешний символ COFF.  
  
 `SymTagUDT`  
 Указывает, что символ определяемых пользователем типов (структуры, класса или объединения).  
  
 `SymTagEnum`  
 Указывает, что символ — это перечисление.  
  
 `SymTagFunctionType`  
 Указывает, что символ является типом подписи функции.  
  
 `SymTagPointerType`  
 Указывает, что символ является типом указателя.  
  
 `SymTagArrayType`  
 Указывает, что символ является типом массива.  
  
 `SymTagBaseType`  
 Указывает, что символ является допустимым базовым типом.  
  
 `SymTagTypedef`  
 Указывает, что символ `typedef`, то есть псевдоним для другого типа.  
  
 `SymTagBaseClass`  
 Указывает, что символ является базовым классом для определяемых пользователем типов.  
  
 `SymTagFriend`  
 Указывает, что символ является дружественный элемент для определяемого пользователем типа.  
  
 `SymTagFunctionArgType`  
 Указывает, что символ является аргументом функции.  
  
 `SymTagFuncDebugStart`  
 Указывает, что символ является конечное расположение кода пролога функции.  
  
 `SymTagFuncDebugEnd`  
 Указывает расположение начала кода эпилога функции символа.  
  
 `SymTagUsingNamespace`  
 Указывает, что символ является имя пространства имен, активных в текущей области.  
  
 `SymTagVTableShape`  
 Указывает, что символ является описание виртуальной таблицы.  
  
 `SymTagVTable`  
 Указывает символ указателя виртуальной таблицы.  
  
 `SymTagCustom`  
 Указывает, что символ — это пользовательский символ и не интерпретируется доступа  
  
 `SymTagThunk`  
 Указывает, что символ является преобразователь, который используется для обмена данными между 16 и 32-разрядная версия кода.  
  
 `SymTagCustomType`  
 Указывает, что символ является символ пользовательских компилятора.  
  
 `SymTagManagedType`  
 Указывает, что символ в метаданных.  
  
 `SymTagDimension`  
 Указывает, что символ является многомерным массивом FORTRAN.  
  
 `SymTagCallSite`  
 Указывает, что символ представляет место вызова.  
  
 `SymTagInlineSite`  
 Указывает, что символ представляет встроенный сайта.  
  
 `SymTagBaseInterface`  
 Указывает, что символ является базовым интерфейсом.  
  
 `SymTagVectorType`  
 Указывает, что символ является тип вектора.  
  
 `SymTagMatrixType`  
 Указывает тип матрицы символ.  
  
 `SymTagHLSLType`  
 Указывает, что символ является типом языка шейдера высокий уровень.  
  
## <a name="remarks"></a>Примечания  
 Все символы в файл отладочных иметь идентифицирующий тег, определяющий тип символа.  
  
 Значения в этом перечислении возвращаются путем вызова [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) метод.  
  
 Значения этого перечисления передаются следующих методов, чтобы ограничить область поиска для типа специальные символы:  
  
-   [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)  
  
-   [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)  
  
-   [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)  
  
-   [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)  
  
-   [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)  
  
-   [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)  
  
-   [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
-   [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
## <a name="requirements"></a>Требования  
 Заголовок: cvconst.h  
  
## <a name="see-also"></a>См. также  
 [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Лексическая иерархия символьных типов](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)   
 [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)   
 [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)   
 [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)   
 [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)   
 [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
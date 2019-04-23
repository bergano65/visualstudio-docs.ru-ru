---
title: SymTagEnum | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- SymTagEnum enumeration
ms.assetid: 528a50cf-e13d-46ec-a98c-323d5d047de9
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1578d88265769414f68964e28d3426ffcc62f9e8
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60092413"
---
# <a name="symtagenum"></a>SymTagEnum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Указывает тип символа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
enum SymTagEnum {   
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
 Указывает, что символ не файл .exe. Имеется только один `SymTagExe` символов в хранилище символов. Он служит в качестве глобальной области и не поддерживает лексические родительского.  
  
 `SymTagCompiland`  
 Указывает символ компилируемого объекта для каждого компонента компилируемого объекта в хранилище символов. Для собственных приложений `SymTagCompiland` символы соответствуют объектные файлы, входящие в образ. Для некоторых видов образов Microsoft Intermediate Language (MSIL) есть в одной единице компиляции каждого класса.  
  
 `SymTagCompilandDetails`  
 Указывает, что символ содержит дополнительные атрибуты единице компиляции. Получение этих свойств может потребоваться загрузка символов единице компиляции.  
  
 `SymTagCompilandEnv`  
 Указывает, что символ не определен для компилируемого объекта строки.  
  
 `SymTagFunction`  
 Указывает, что символ является функцией.  
  
 `SymTagBlock`  
 Указывает, что символ не вложенный блок.  
  
 `SymTagData`  
 Указывает, что символ не данных.  
  
 `SymTagAnnotation`  
 Указывает, что символ не для заметки в виде кода. Дочерние элементы этого символа, представляют собой постоянные данные строки (`SymTagData`, `LocIsConstant`, `DataIsConstant`). Большинство клиентов игнорировать этот символ.  
  
 `SymTagLabel`  
 Указывает, что символ не метки.  
  
 `SymTagPublicSymbol`  
 Указывает, что символ не открытого символа. Для собственных приложений этот символ используется внешний символ COFF, при связывании изображение.  
  
 `SymTagUDT`  
 Указывает, что символ не определяемого пользователем типа (структуры, класса или объединения).  
  
 `SymTagEnum`  
 Указывает, что символ является перечислением.  
  
 `SymTagFunctionType`  
 Указывает, что символ не является типом сигнатуры функции.  
  
 `SymTagPointerType`  
 Указывает, что символ является типом указателя.  
  
 `SymTagArrayType`  
 Указывает, что символ не является массивом.  
  
 `SymTagBaseType`  
 Указывает, что символ не является базовым типом.  
  
 `SymTagTypedef`  
 Указывает, что символ не `typedef`, то есть псевдонимом для другого типа.  
  
 `SymTagBaseClass`  
 Указывает, что символ не базовый класс для определяемого пользователем типа.  
  
 `SymTagFriend`  
 Указывает, что символ является дружественной для определяемого пользователем типа.  
  
 `SymTagFunctionArgType`  
 Указывает, что символ не является аргументом функции.  
  
 `SymTagFuncDebugStart`  
 Указывает, что символ не конечное расположение кода пролога функции.  
  
 `SymTagFuncDebugEnd`  
 Указывает, что символ не расположение начала кода эпилога функции.  
  
 `SymTagUsingNamespace`  
 Указывает, что символ является имя пространства имен, активных в текущей области.  
  
 `SymTagVTableShape`  
 Указывает, что символ является описание виртуальной таблицы.  
  
 `SymTagVTable`  
 Указывает, что символ является указатель виртуальной таблицы.  
  
 `SymTagCustom`  
 Указывает, что символ — это пользовательский символ и не интерпретируется DIA.  
  
 `SymTagThunk`  
 Указывает, что символ является преобразователь, который используется для обмена данными между 16- и 32-разрядная версия кода.  
  
 `SymTagCustomType`  
 Указывает, что символ является символом собственный компилятор.  
  
 `SymTagManagedType`  
 Указывает, что символ не в метаданных.  
  
 `SymTagDimension`  
 Указывает, что символ является многомерным массивом FORTRAN.  
  
 `SymTagCallSite`  
 Указывает, что символ представляет источник вызова.  
  
 `SymTagInlineSite`  
 Указывает, что символ представляет встроенный сайта.  
  
 `SymTagBaseInterface`  
 Указывает, что символ — это базовый интерфейс.  
  
 `SymTagVectorType`  
 Указывает, что символ не является векторным типом.  
  
 `SymTagMatrixType`  
 Указывает, что символ относится к типу матрицы.  
  
 `SymTagHLSLType`  
 Указывает, что символ относится к типу High Level Shader Language.  
  
## <a name="remarks"></a>Примечания  
 Все символы в файле отладки иметь тег идентификации, указывающее тип символа.  
  
 Значения в этом перечислении возвращаются путем вызова [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) метод.  
  
 Значения в этом перечислении передаются в следующие методы, чтобы ограничить область поиска до типа конкретного символа:  
  
- [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)  
  
- [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)  
  
- [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)  
  
- [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)  
  
- [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)  
  
- [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)  
  
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
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

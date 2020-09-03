---
title: Симтаженум | Документация Майкрософт
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193518"
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
 Указывает, что символ является EXE-файлом. `SymTagExe`Для хранилища символов существует только один символ. Он служит глобальной областью и не имеет лексического родителя.  
  
 `SymTagCompiland`  
 Указывает символ компилируемого объекта для каждого компонента компилируемого объекта хранилища символов. Для собственных приложений `SymTagCompiland` символы соответствуют объектным файлам, связанным с изображением. Для некоторых типов образов MSIL существует один компилируемого объекта для каждого класса.  
  
 `SymTagCompilandDetails`  
 Указывает, что символ содержит расширенные атрибуты компилируемого объекта. Для получения этих свойств может потребоваться загрузка компилируемого объекта символов.  
  
 `SymTagCompilandEnv`  
 Указывает, что символ — это строка среды, определенная для компилируемого объекта.  
  
 `SymTagFunction`  
 Указывает, что символ является функцией.  
  
 `SymTagBlock`  
 Указывает, что символ является вложенным блоком.  
  
 `SymTagData`  
 Указывает, что символ является данными.  
  
 `SymTagAnnotation`  
 Указывает, что символ относится к заметке кода. Дочерние элементы этого символа представляют собой постоянные строки данных ( `SymTagData` , `LocIsConstant` , `DataIsConstant` ). Большинство клиентов игнорируют этот символ.  
  
 `SymTagLabel`  
 Указывает, что символ является меткой.  
  
 `SymTagPublicSymbol`  
 Указывает, что символ является открытым символом. Для собственных приложений этот символ является внешним символом COFF, обнаруженным при связывании изображения.  
  
 `SymTagUDT`  
 Указывает, что символ является определяемым пользователем типом (структурой, классом или объединением).  
  
 `SymTagEnum`  
 Указывает, что символ является перечислением.  
  
 `SymTagFunctionType`  
 Указывает, что символ является типом сигнатуры функции.  
  
 `SymTagPointerType`  
 Указывает, что символ является типом указателя.  
  
 `SymTagArrayType`  
 Указывает, что символ является типом массива.  
  
 `SymTagBaseType`  
 Указывает, что символ является базовым типом.  
  
 `SymTagTypedef`  
 Указывает, что символ — это `typedef` псевдоним для другого типа.  
  
 `SymTagBaseClass`  
 Указывает, что символ является базовым классом определяемого пользователем типа.  
  
 `SymTagFriend`  
 Указывает, что символ является дружественным для определяемого пользователем типа.  
  
 `SymTagFunctionArgType`  
 Указывает, что символ является аргументом функции.  
  
 `SymTagFuncDebugStart`  
 Указывает, что символ является конечным расположением кода пролога функции.  
  
 `SymTagFuncDebugEnd`  
 Указывает, что символ является начальным расположением кода эпилога функции.  
  
 `SymTagUsingNamespace`  
 Указывает, что символ является именем пространства имен, активным в текущей области.  
  
 `SymTagVTableShape`  
 Указывает, что символ является описанием виртуальной таблицы.  
  
 `SymTagVTable`  
 Указывает, что символ является указателем виртуальной таблицы.  
  
 `SymTagCustom`  
 Указывает, что символ является пользовательским символом и не интерпретируется DIA.  
  
 `SymTagThunk`  
 Указывает, что символ — это преобразователь, используемый для обмена данными между 16 и 32 битным кодом.  
  
 `SymTagCustomType`  
 Указывает, что символ является пользовательским символом компилятора.  
  
 `SymTagManagedType`  
 Указывает, что символ находится в метаданных.  
  
 `SymTagDimension`  
 Указывает, что символ является многомерным массивом FORTRAN.  
  
 `SymTagCallSite`  
 Указывает, что символ представляет сайт вызова.  
  
 `SymTagInlineSite`  
 Указывает, что символ представляет встроенный веб-сайт.  
  
 `SymTagBaseInterface`  
 Указывает, что символ является базовым интерфейсом.  
  
 `SymTagVectorType`  
 Указывает, что символ является векторным типом.  
  
 `SymTagMatrixType`  
 Указывает, что символ является типом матрицы.  
  
 `SymTagHLSLType`  
 Указывает, что символ является типом языка шейдера высокого уровня.  
  
## <a name="remarks"></a>Remarks  
 Все символы в файле отладки имеют идентифицирующий тег, указывающий тип символа.  
  
 Значения в этом перечислении возвращаются путем вызова метода [IDiaSymbol:: get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) .  
  
 Значения в этом перечислении передаются следующим методам для ограничения области поиска конкретным типом символа:  
  
- [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)  
  
- [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)  
  
- [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)  
  
- [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)  
  
- [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)  
  
- [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)  
  
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
## <a name="requirements"></a>Требования  
 Заголовок: квконст. h  
  
## <a name="see-also"></a>См. также:  
 [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Лексическая иерархия типов символов](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [IDiaSession:: Финдсимболбяддр](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)   
 [IDiaSession:: Финдсимболбирва](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)   
 [IDiaSession:: Финдсимболбирваекс](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)   
 [IDiaSession:: Финдсимболбитокен](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)   
 [IDiaSession:: Финдсимболбива](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)   
 [IDiaSession:: Финдсимболбиваекс](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)   
 [IDiaSession:: Финдчилдрен](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)

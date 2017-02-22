---
title: "SymTagEnum | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SymTagEnum - перечисление"
ms.assetid: 528a50cf-e13d-46ec-a98c-323d5d047de9
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# SymTagEnum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Указывает тип символа.  
  
## Синтаксис  
  
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
  
## Elements  
 `SymTagNull`  
 Указывает, что символ не имеет типа.  
  
 `SymTagExe`  
 Указывает, что знак является EXE\-файл.  Только один `SymTagExe` символ в хранилище символов.  Он служит в качестве глобальной области действия и не имеет лексическую родительского.  
  
 `SymTagCompiland`  
 Указывает символ компиляции для каждого компонента единица компиляции в хранилище символов.  Для приложений `SymTagCompiland` символы соответствуют объектных файлов, связанных в изображение.  Для некоторых видов изображений промежуточного языка MSIL не существует одна единица компиляции каждого класса.  
  
 `SymTagCompilandDetails`  
 Показывает, что символ содержит расширенные атрибуты компилируемом компоненте.  Получение этих свойств может потребоваться загрузка символов единицы компиляции.  
  
 `SymTagCompilandEnv`  
 Указывает, что символ строки среды, определенные для компиляции.  
  
 `SymTagFunction`  
 Указывает, что символ функции.  
  
 `SymTagBlock`  
 Указывает, что символ вложенного блока.  
  
 `SymTagData`  
 Указывает, что символ данных.  
  
 `SymTagAnnotation`  
 Указывает, что для пометки кода символа.  Дети от этого символа, постоянные данные строки \(`SymTagData`, `LocIsConstant`, `DataIsConstant`\).  Большинство клиентов игнорировать этот символ.  
  
 `SymTagLabel`  
 Указывает, что символ метки.  
  
 `SymTagPublicSymbol`  
 Указывает, что символ открытых символов.  Для приложений этот символ используется внешний символ COFF, при связывании изображения.  
  
 `SymTagUDT`  
 Указывает, что символ определяемого пользователем типа \(структуры, класса или объединения\).  
  
 `SymTagEnum`  
 Указывает, что символ перечисления.  
  
 `SymTagFunctionType`  
 Указывает тип подписи функции символа.  
  
 `SymTagPointerType`  
 Указывает тип указателя символа.  
  
 `SymTagArrayType`  
 Указывает, что символ типа массива.  
  
 `SymTagBaseType`  
 Указывает базовый тип символа.  
  
 `SymTagTypedef`  
 Указывает, что символ `typedef`, то есть псевдоним для другого типа.  
  
 `SymTagBaseClass`  
 Указывает, что символ базового класса определяемого пользователем типа.  
  
 `SymTagFriend`  
 Указывает, что символ friend определяемого пользователем типа.  
  
 `SymTagFunctionArgType`  
 Указывает, что символ аргумента функции.  
  
 `SymTagFuncDebugStart`  
 Указывает, что символ конца расположение кода пролога функции.  
  
 `SymTagFuncDebugEnd`  
 Указывает, что символ начала расположение код эпилога функции.  
  
 `SymTagUsingNamespace`  
 Указывает символ в имени пространства имен в текущей области.  
  
 `SymTagVTableShape`  
 Указывает, что символ Описание виртуальной таблицы.  
  
 `SymTagVTable`  
 Указывает, что символ указателя виртуальной таблицы.  
  
 `SymTagCustom`  
 Указывает, что символ — это пользовательский символ и воспринимается не DIA.  
  
 `SymTagThunk`  
 Указывает, что символ преобразователь, используется для обмена данными между 16 и 32\-разрядного кода.  
  
 `SymTagCustomType`  
 Указывает, что символ символ пользовательских компилятора.  
  
 `SymTagManagedType`  
 Указывает, что символ в метаданных.  
  
 `SymTagDimension`  
 Указывает, что символ FORTRAN многомерный массив.  
  
 `SymTagCallSite`  
 Указывает, что символ представляет вызов узла.  
  
 `SymTagInlineSite`  
 Указывает, что символ представляет встроенный веб\-узла.  
  
 `SymTagBaseInterface`  
 Указывает, что символ базового интерфейса.  
  
 `SymTagVectorType`  
 Указывает, что символ типа vector.  
  
 `SymTagMatrixType`  
 Указывает, что символ типа матрицы.  
  
 `SymTagHLSLType`  
 Указывает, что символ типа язык шейдера высокого уровня.  
  
## Заметки  
 Все символы в файле отладки иметь идентифицирующий тег, который задает тип символа.  
  
 Значения в этом перечислении возвращаются с помощью вызова [IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md) метод.  
  
 Значения из этого перечисления передаются следующие методы для ограничения области поиска определенного символа типа:  
  
-   [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)  
  
-   [IDiaSession::findSymbolByRVA](../Topic/IDiaSession::findSymbolByRVA.md)  
  
-   [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)  
  
-   [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)  
  
-   [IDiaSession::findSymbolByVA](../Topic/IDiaSession::findSymbolByVA.md)  
  
-   [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)  
  
-   [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
-   [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
## Требования  
 Заголовок: cvconst.h  
  
## См. также  
 [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Лексическая иерархия символьных типов](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)   
 [IDiaSession::findSymbolByRVA](../Topic/IDiaSession::findSymbolByRVA.md)   
 [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)   
 [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)   
 [IDiaSession::findSymbolByVA](../Topic/IDiaSession::findSymbolByVA.md)   
 [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
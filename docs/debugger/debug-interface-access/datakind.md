---
title: DataKind | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DataKind enumeration
ms.assetid: b64be708-22d6-4360-99e7-8f4e6b196de7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 508058a85d60645fca5e50bc1e6c456da7df7b26
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="datakind"></a>DataKind
Указывает, определенной областью значение данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
enum DataKind {   
   DataIsUnknown,  
   DataIsLocal,  
   DataIsStaticLocal,  
   DataIsParam,  
   DataIsObjectPtr,  
   DataIsFileStatic,  
   DataIsGlobal,  
   DataIsMember,  
   DataIsStaticMember,  
   DataIsConstant  
};  
```  
  
## <a name="elements"></a>Элементы  
 DataIsUnknown  
 Не удается определить символ данных.  
  
 DataIsLocal  
 Элемент данных является локальной переменной.  
  
 DataIsStaticLocal  
 Элемент данных является статической локальной переменной.  
  
 DataIsParam  
 Элемент данных относится формальных параметров.  
  
 DataIsObjectPtr  
 Элемент данных является указатель на объект (`this`).  
  
 DataIsFileStatic  
 Элемент данных относится переменную видимой в пределах файла.  
  
 DataIsGlobal  
 Элемент данных является глобальной переменной.  
  
 DataIsMember  
 Элемент данных относится переменная члена объекта.  
  
 DataIsStaticMember  
 Элемент данных является статической переменной класса.  
  
 DataIsConstant  
 Элемент данных имеет постоянное значение.  
  
## <a name="remarks"></a>Примечания  
 Возвращаемые значения в этом перечислении [IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md) метод.  
  
## <a name="requirements"></a>Требования  
 Заголовок: cvconst.h  
  
## <a name="see-also"></a>См. также  
 [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)
---
title: Kind | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- DataKind enumeration
ms.assetid: b64be708-22d6-4360-99e7-8f4e6b196de7
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a6a72d1093bc8acd9aae788ff357aee2efeb9e52
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197637"
---
# <a name="datakind"></a>DataKind
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Указывает конкретную область значения данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
enum DataKind {   
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
 датаисункновн  
 Не удается определить символ данных.  
  
 датаислокал  
 Элемент данных является локальной переменной.  
  
 датаисстатиклокал  
 Элемент данных является статической локальной переменной.  
  
 датаиспарам  
 Элемент данных является формальным параметром.  
  
 DataIsObjectPtr  
 Элемент данных является указателем объекта ( `this` ).  
  
 DataIsFileStatic  
 Элемент данных является переменной с областью действия файла.  
  
 датаисглобал  
 Элемент данных является глобальной переменной.  
  
 датаисмембер  
 Элемент данных является переменной-членом объекта.  
  
 датаисстатикмембер  
 Элемент данных — это статическая переменная класса.  
  
 датаисконстант  
 Элемент данных является постоянным значением.  
  
## <a name="remarks"></a>Remarks  
 Значения в этом перечислении возвращаются методом [IDiaSymbol:: get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md) .  
  
## <a name="requirements"></a>Требования  
 Заголовок: квконст. h  
  
## <a name="see-also"></a>См. также:  
 [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)

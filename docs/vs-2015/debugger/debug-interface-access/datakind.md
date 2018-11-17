---
title: DataKind | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- DataKind enumeration
ms.assetid: b64be708-22d6-4360-99e7-8f4e6b196de7
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 93c67b0199524072bf45558dc1713c760567495c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51760470"
---
# <a name="datakind"></a>DataKind
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Указывает область конкретного значения данных.  
  
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
 DataIsUnknown  
 Не удается определить символ данных.  
  
 DataIsLocal  
 Элемент данных — это локальная переменная.  
  
 DataIsStaticLocal  
 Элемент данных является статической локальной переменной.  
  
 DataIsParam  
 Элемент данных является формальным параметром.  
  
 DataIsObjectPtr  
 Элемент данных является указателем объекта (`this`).  
  
 DataIsFileStatic  
 Элемент данных — это переменная уровня файла.  
  
 DataIsGlobal  
 Элемент данных является глобальной переменной.  
  
 DataIsMember  
 Элемент данных является переменной члена объекта.  
  
 DataIsStaticMember  
 Элемент данных является статической переменной класса.  
  
 DataIsConstant  
 Элемент данных — это постоянное значение.  
  
## <a name="remarks"></a>Примечания  
 Возвращаемые значения в этом перечислении [IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md) метод.  
  
## <a name="requirements"></a>Требования  
 Заголовок: cvconst.h  
  
## <a name="see-also"></a>См. также  
 [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)




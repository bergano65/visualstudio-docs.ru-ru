---
title: "DataKind | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: DataKind enumeration
ms.assetid: b64be708-22d6-4360-99e7-8f4e6b196de7
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7fecbec475aee44efd9a91a24ec933dbbbcb17e9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
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
---
title: "IDiaSectionContrib::get_comdat | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSectionContrib::get_comdat method
ms.assetid: 8bd9be8d-59ee-4698-b055-daba354b8dcc
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d3797f60e9ca6e97da3b7b6e44c89f802b086d13
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idiasectioncontribgetcomdat"></a>IDiaSectionContrib::get_comdat
Возвращает флаг, который указывает, является ли раздел записи COMDAT.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_comdat (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает `TRUE` Если раздел записи COMDAT; в противном случае возвращает `FALSE`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` , если это свойство не поддерживается. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Записи COMDAT является общий объект файла формат COFF запись, которая делает упакованные функции видимым в компоновщик.  
  
## <a name="see-also"></a>См. также  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)
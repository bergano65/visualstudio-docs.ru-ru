---
title: "IDiaSymbol::get_acceleratorPointerTags | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 30e13cee-e511-49ec-affd-99b0097071b2
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e5190496258cfb4ed66334e10a3d727a1c9555b6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idiasymbolgetacceleratorpointertags"></a>IDiaSymbol::get_acceleratorPointerTags
Возвращает все значения тега указатель сочетаний клавиш, соответствующие функции C++ AMP заглушки сочетаний клавиш.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_acceleratorPointerTags(   
   DWORD          cnt,  
   DWORD*         pcnt,  
   DWORD*         pPointerTags);  
```  
  
#### <a name="parameters"></a>Параметры  
 `cnt`  
 [in] Размер выходного массива `pPointerTags`.  
  
 `pcnt`  
 [out] Счетчик тегов указатель сочетаний клавиш в C++ AMP функции заглушки сочетаний клавиш.  
  
 `pPointerTags`  
 [out] Объект `DWORD` указатель на массив, который заполняется значениями тег указателей сочетаний клавиш в C++ AMP функции заглушки сочетаний клавиш.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод вызывается для `IDiaSymbol` интерфейс, который соответствует функции C++ AMP заглушки сочетаний клавиш.  
  
## <a name="see-also"></a>См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
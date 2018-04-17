---
title: IDiaSymbol::get_acceleratorPointerTags | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 30e13cee-e511-49ec-affd-99b0097071b2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 159464305063fd2d40109ba000421f0e5cc72d09
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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
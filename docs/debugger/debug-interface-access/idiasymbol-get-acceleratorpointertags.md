---
title: IDiaSymbol::get_acceleratorPointerTags | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 30e13cee-e511-49ec-affd-99b0097071b2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5e65def0ac8e94b2f113332981f57c051896f6bd
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53875463"
---
# <a name="idiasymbolgetacceleratorpointertags"></a>IDiaSymbol::get_acceleratorPointerTags
Возвращает все значения тега указатель сочетаний клавиш, которые соответствуют на функцию C++ AMP accelerator заглушки.  
  
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
 [out] Число тегов указатель сочетаний клавиш в функцию C++ AMP accelerator заглушки.  
  
 `pPointerTags`  
 [out] Объект `DWORD` указатель на массив, заполненный со значениями тегов accelerator указателя в функцию C++ AMP accelerator заглушки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод вызывается на `IDiaSymbol` интерфейс, который соответствует функции заглушки accelerator C++ AMP.  
  
## <a name="see-also"></a>См. также раздел  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
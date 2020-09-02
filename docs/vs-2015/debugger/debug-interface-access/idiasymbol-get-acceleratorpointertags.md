---
title: 'IDiaSymbol:: get_acceleratorPointerTags | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: 30e13cee-e511-49ec-affd-99b0097071b2
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 829c7a0193ce2742959f677e95dd4a499997cf5b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149844"
---
# <a name="idiasymbolget_acceleratorpointertags"></a>IDiaSymbol::get_acceleratorPointerTags
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Возвращает все значения тегов указателя ускорителя, соответствующие функции-заглушке C++ AMP ускорителя.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT get_acceleratorPointerTags(   
   DWORD          cnt,  
   DWORD*         pcnt,  
   DWORD*         pPointerTags);  
```  
  
#### <a name="parameters"></a>Параметры  
 `cnt`  
 окне Размер выходного массива `pPointerTags` .  
  
 `pcnt`  
 заполняет Число тегов указателя ускорителя в функции-заглушке C++ AMP ускорителе.  
  
 `pPointerTags`  
 заполняет `DWORD` Указатель массива, который заполняется значениями тега указателя-ускорителя в функции-заглушке C++ amp ускорителе.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK` ; в противном случае возвращает `S_FALSE` или код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Этот метод вызывается для `IDiaSymbol` интерфейса, который соответствует функции-заглушке C++ amp ускорителя.  
  
## <a name="see-also"></a>См. также:  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)

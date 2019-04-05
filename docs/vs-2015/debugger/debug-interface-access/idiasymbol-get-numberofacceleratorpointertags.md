---
title: IDiaSymbol::get_numberOfAcceleratorPointerTags | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: 1886e3ec-b227-4187-8d93-c5144b4b77ae
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b25cd941b8f06909ca1bf777d0e3251c78732706
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58989851"
---
# <a name="idiasymbolgetnumberofacceleratorpointertags"></a>IDiaSymbol::get_numberOfAcceleratorPointerTags
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Возвращает число тегов указатель сочетаний клавиш в функции заглушки C++ AMP.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT get_numberOfAcceleratorPointerTags(   
   DWORD* count);  
```  
  
#### <a name="parameters"></a>Параметры  
 `count`  
 [out] Указатель на `DWORD` , содержащий количество сочетаний клавиш теги указателя в функцию C++ AMP заглушки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод вызывается на `IDiaSymbol` интерфейс, который соответствует функции заглушки accelerator C++ AMP.  
  
## <a name="see-also"></a>См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)

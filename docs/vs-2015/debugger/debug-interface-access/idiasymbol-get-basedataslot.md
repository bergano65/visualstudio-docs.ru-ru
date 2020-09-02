---
title: 'IDiaSymbol:: get_baseDataSlot | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: f9ed21b7-9397-4813-926e-ade11914b06b
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d0fbdf2bf6df2e61e1328a71f180264d582bfdf9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149819"
---
# <a name="idiasymbolget_basedataslot"></a>IDiaSymbol::get_baseDataSlot
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Извлекает базовый слот данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT get_baseDataSlot(   
   DWORD* pRetVal);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 заполняет Указатель на объект `DWORD` , содержащий базовый слот данных.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK` ; в противном случае возвращает `S_FALSE` или код ошибки.  
  
## <a name="see-also"></a>См. также:  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)

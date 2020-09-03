---
title: 'Идиаенумсимболсбяддр:: Симболбяддр | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsByAddr::symbolByAddr method
ms.assetid: 0b6f5a68-8402-4f29-8219-20576fda8166
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6561c3afd273a2a559138ed2363b4ffa4fdd0fd8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189610"
---
# <a name="idiaenumsymbolsbyaddrsymbolbyaddr"></a>IDiaEnumSymbolsByAddr::symbolByAddr
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Размещает перечислитель, выполняя поиск по номеру и смещению раздела изображения.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT symbolByAddr (   
   DWORD**      isect,  
   DWORD**      offsect,  
   IDiaSymbol** ppsymbol  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 исект  
 окне Номер раздела изображения.  
  
 оффсект  
 окне Смещение в разделе.  
  
 ппсимбол  
 заполняет Возвращает объект [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , представляющий найденный символ.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` , если не удалось найти символ. В противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также:  
 [идиаенумсимболсбяддр](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)

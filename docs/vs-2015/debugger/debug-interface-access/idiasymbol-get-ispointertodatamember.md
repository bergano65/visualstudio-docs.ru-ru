---
title: 'IDiaSymbol:: get_isPointerToDataMember | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: ef17c737-242e-43e8-b7e1-2c3bc58cfcef
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ca44d11dfcec717e37a9bc13a2d87f9f5a94ede3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155881"
---
# <a name="idiasymbolget_ispointertodatamember"></a>IDiaSymbol::get_isPointerToDataMember
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Указывает, является ли этот символ указателем на элемент данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT get_isPointerToDataMember(   
   BOOL* pRetVal);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 заполняет Указатель на объект `BOOL` , указывающий, является ли этот символ указателем на элемент данных.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK` ; в противном случае возвращает `S_FALSE` или код ошибки.  
  
## <a name="see-also"></a>См. также:  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)

---
title: 'Идиалоадкаллбакк:: Рестриктсимболсерверакцесс | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::RestrictSymbolServerAccess method
ms.assetid: db37ad9f-f75e-4f0c-83bf-21a6e66ba859
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fddf9812810e7d184859f60d98f51000b824092a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150600"
---
# <a name="idialoadcallbackrestrictsymbolserveraccess"></a>IDiaLoadCallback::RestrictSymbolServerAccess
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Определяет, разрешен ли доступ к серверу символов для разрешения символов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT RestrictSymbolServerAccess();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Любой код возврата, отличный от, `S_OK` не позволяет использовать сервер символов для разрешения символов.  
  
## <a name="see-also"></a>См. также:  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)

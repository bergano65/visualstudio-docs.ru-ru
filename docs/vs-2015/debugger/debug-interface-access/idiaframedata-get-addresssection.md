---
title: IDiaFrameData::get_addressSection | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_addressSection method
ms.assetid: e4eedede-4a1c-4da2-a812-b92df328fd8d
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1efc55899978280711ea608824d34c47ad01ad5e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47561960"
---
# <a name="idiaframedatagetaddresssection"></a>IDiaFrameData::get_addressSection
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDiaFrameData::get_addressSection](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiaframedata-get-addresssection).  
  
Получает раздел часть адреса кода для кадра.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT get_addressSection (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает раздел часть адреса кода для кадра.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`. Возвращает `S_FALSE` Если это свойство не поддерживается. В противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)




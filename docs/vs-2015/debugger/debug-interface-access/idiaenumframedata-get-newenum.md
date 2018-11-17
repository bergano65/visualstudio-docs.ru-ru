---
title: IDiaEnumFrameData::get__NewEnum | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
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
- IDiaEnumFrameData::get__NewEnum method
ms.assetid: f5fe0279-0549-4af5-8f89-bcb535fc5809
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 32eb823bbb5cc32ded254d847857756ccf0ddef1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51724024"
---
# <a name="idiaenumframedatagetnewenum"></a>IDiaEnumFrameData::get__NewEnum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Извлекает <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> версии этот перечислитель.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT get__NewEnum (   
   IUnknown** pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 pRetVal  
 [out] Возвращает `IUnknown` интерфейс, который представляет <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> версии этот перечислитель.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)




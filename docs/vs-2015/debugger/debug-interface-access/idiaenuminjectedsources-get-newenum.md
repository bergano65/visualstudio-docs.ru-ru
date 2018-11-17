---
title: IDiaEnumInjectedSources::get__NewEnum | Документация Майкрософт
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
- IDiaEnumInjectedSources::get__NewEnum method
ms.assetid: f56cdcdb-dc71-43c7-82fe-e2500986f5bc
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e0adfad330ff3bf637558781ad244e407da6ef02
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51766203"
---
# <a name="idiaenuminjectedsourcesgetnewenum"></a>IDiaEnumInjectedSources::get__NewEnum
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
 [out, retval] Возвращает `IUnknown` интерфейс, который представляет <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> версии этот перечислитель.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)




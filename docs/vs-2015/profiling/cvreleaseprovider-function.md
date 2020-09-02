---
title: Функция CvReleaseProvider | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- cvmarkers/CvReleaseProvider
helpviewer_keywords:
- CvReleaseProvider method
ms.assetid: 8d74379e-295d-452b-bd5f-0769df387d4f
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7d5e611c2a964fcbb78a387a09989436e672ecd6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62551238"
---
# <a name="cvreleaseprovider-function"></a>Функция CvReleaseProvider
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Освобождает поставщик маркеров. Освобождение поставщика маркеров не повлияет на ранее созданный набор маркеров данного поставщика. Наборы маркеров должны быть выпущены раздельно вызовом функции CvReleaseMarkerSeries. Сбой при освобождении поставщика маркеров приводит к утечке памяти.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT CvReleaseProvider(  
   _In_ PCV_PROVIDER pProvider  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pProvider`  
 Контекст поставщика. Не может принимать значение NULL.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение S_OK, если поставщик успешно освобожден, или код ошибки, если были какие-либо ошибки. Для проверки условия ошибки используйте макрос SUCCEEDED/FAILED.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** cvmarkers.h  
  
## <a name="see-also"></a>См. также:  
 [Справочник по библиотеке C++](../profiling/cpp-library-reference.md)

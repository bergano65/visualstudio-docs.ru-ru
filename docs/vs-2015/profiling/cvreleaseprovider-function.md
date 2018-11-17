---
title: Функция CvReleaseProvider | Документы Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- cvmarkers/CvReleaseProvider
helpviewer_keywords:
- CvReleaseProvider method
ms.assetid: 8d74379e-295d-452b-bd5f-0769df387d4f
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2c59e5516129d5712983a228f68e4e91301656c2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51738818"
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
  
## <a name="see-also"></a>См. также  
 [Справочник по библиотеке C++](../profiling/cpp-library-reference.md)




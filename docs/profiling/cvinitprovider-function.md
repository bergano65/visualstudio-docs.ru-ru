---
title: "Функция CvInitProvider | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: cvmarkers/CvInitProvider
helpviewer_keywords: CvInitProvider method
ms.assetid: ba1863ad-e35f-4d34-a2f2-5e68957d1915
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0ddb249c825048b5bb98dd5b648902663ccd85a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="cvinitprovider-function"></a>Функция CvInitProvider
Инициализирует поставщик маркеров. Должна быть вызвана до любой другой функции пакета SDK визуализатора параллелизма.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT CvInitProvider(  
   _In_ const GUID* pGuid,  
   _Out_ PCV_PROVIDER* ppProvider  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pGuid`  
 GUID поставщика. Не может принимать значение NULL.  
  
 `ppProvider`  
 Адрес выходной переменной, в которой будет храниться контекст поставщика. Не может принимать значение NULL.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение S_OK, если поставщик успешно инициализирован, или код ошибки, если были какие-либо ошибки. Для проверки условия ошибки используйте макрос SUCCEEDED/FAILED.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** cvmarkers.h  
  
## <a name="see-also"></a>См. также  
 [Справочник по библиотеке C++](../profiling/cpp-library-reference.md)
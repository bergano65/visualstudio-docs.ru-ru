---
title: Функция CvInitProvider | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvInitProvider
helpviewer_keywords:
- CvInitProvider method
ms.assetid: ba1863ad-e35f-4d34-a2f2-5e68957d1915
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2fed378aad3a988daa532bb22c0dfd6cb3cbfd2f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54923234"
---
# <a name="cvinitprovider-function"></a>Функция CvInitProvider
Инициализирует поставщик маркеров. Должна быть вызвана до любой другой функции пакета SDK визуализатора параллелизма.  
  
## <a name="syntax"></a>Синтаксис  
  
```C  
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
 **Заголовок:** *cvmarkers.h*  
  
## <a name="see-also"></a>См. также  
 [Справочник по библиотеке C++](../profiling/cpp-library-reference.md)
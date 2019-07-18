---
title: Функция CvInitProvider | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- cvmarkers/CvInitProvider
helpviewer_keywords:
- CvInitProvider method
ms.assetid: ba1863ad-e35f-4d34-a2f2-5e68957d1915
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a5a8a9e70c85563e95037c754c59b6077ed21f28
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2019
ms.locfileid: "54771873"
---
# <a name="cvinitprovider-function"></a>Функция CvInitProvider
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
  
## <a name="see-also"></a>См. также раздел  
 [Справочник по библиотеке C++](../profiling/cpp-library-reference.md)

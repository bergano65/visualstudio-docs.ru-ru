---
title: Функция CvWriteFlag | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- cvmarkers/CvWriteFlagExVA
- cvmarkers/CvWriteFlagExW
- cvmarkers/CvWriteFlagExVW
- cvmarkers/CvWriteFlagExA
helpviewer_keywords:
- CvWriteFlagExW method
- CvWriteFlagExVA method
- CvWriteFlagExA method
- CvWriteFlagExVW method
ms.assetid: ee9da1e2-7b34-4cba-81e2-215d25d32e4d
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bea5e2acea9a89c5a3b2fdfba441530a74ad8515
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "54779153"
---
# <a name="cvwriteflag-function"></a>Функция CvWriteFlag
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Записывает флаг в файл трассировки визуализатора параллелизма.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT CvWriteFlagExW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ CV_IMPORTANCE level,  
    _In_ int category,  
    _In_ PCWSTR pMessage,  
    ...  
    );  
  
HRESULT CvWriteFlagExA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ CV_IMPORTANCE level,  
    _In_ int category,  
    _In_ PCSTR pMessage,  
    ...  
    );  
  
HRESULT CvWriteFlagExVW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ CV_IMPORTANCE level,  
    _In_ int category,  
    _In_ PCWSTR pMessage,  
    _In_ va_list argList);  
  
HRESULT CvWriteFlagExVA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ CV_IMPORTANCE level,  
    _In_ int category,  
    _In_ PCSTR pMessage,  
    _In_ va_list argList);  
```  
  
#### <a name="parameters"></a>Параметры  
 `argList`  
 Список аргументов.  
  
 `category`  
 Категория.  
  
 `level`  
 Уровень важности.  
  
 `pMarkerSeries`  
 Допустимый контекст набора маркеров. Не может принимать значение NULL.  
  
 `pMessage`  
 Строка формата сообщений. Не может принимать значение NULL.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение S_OK, если сообщение успешно записано. Код ошибки в том случае, если были какие-либо ошибки. Для проверки условия ошибки используйте макрос SUCCEEDED/FAILED.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** cvmarkers.h  
  
 **Юникод:** CvWriteFlagExW, CvWriteFlagExVW  
  
 <strong>ANSI:</strong>CvWriteFlagExA, CvWriteFlagExVA  
  
## <a name="see-also"></a>См. также раздел  
 [Справочник по библиотеке C++](../profiling/cpp-library-reference.md)

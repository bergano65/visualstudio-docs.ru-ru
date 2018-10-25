---
title: IDiaImageData::get_imageBase | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaImageData::get_imageBase method
ms.assetid: 4ba3d9e4-b205-4ee6-a41d-6996972f1f85
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6e0037ef4bbbfc499d23e517e0fb3522b8f042c7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49822988"
---
# <a name="idiaimagedatagetimagebase"></a>IDiaImageData::get_imageBase
Получает область памяти, в котором должно основываться изображение.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_imageBase (   
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает базовое значение предлагаемые образа.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Из-за конфликтов базовый образ образ может изменения перемещены из автоматически опции неиспользуемой памяти при загрузке. Этот метод возвращает базовый указание (Рекомендуемый объем памяти расположение), которое было сохранено в модуле во время компиляции.  
  
## <a name="see-also"></a>См. также  
 [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)
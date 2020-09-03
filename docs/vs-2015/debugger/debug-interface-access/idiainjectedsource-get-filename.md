---
title: 'Идиаинжектедсаурце:: get_filename | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_filename method
ms.assetid: 20f4fc68-335a-4971-b3a6-76501f0e8b19
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 68db108fe6193517d26957fd74807c2ed2b89035
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161390"
---
# <a name="idiainjectedsourceget_filename"></a>IDiaInjectedSource::get_filename
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Возвращает имя файла для источника.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT get_filename (   
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 претвал  
 заполняет Возвращает имя файла для источника.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` , если это свойство не поддерживается. В противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также:  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)

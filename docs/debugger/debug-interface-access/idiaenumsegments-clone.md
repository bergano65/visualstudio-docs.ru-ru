---
title: IDiaEnumSegments::Clone | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::Clone method
ms.assetid: 93deaac6-72ab-4408-ba14-66174a618757
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f2e8faf0d9a933ba9ce08824de5bc9f6dc6d8d44
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idiaenumsegmentsclone"></a>IDiaEnumSegments::Clone
Создает перечислитель, с тем же состоянием, как у текущего перечислителя.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT Clone (   
   IDiaEnumSegments** ppenum  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 ppenum  
 [out] Возвращает [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md) объект, который содержит повторяющийся перечислителя. Сегменты не повторяются, только перечислитель.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)
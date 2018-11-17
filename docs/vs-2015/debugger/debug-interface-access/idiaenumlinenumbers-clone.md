---
title: IDiaEnumLineNumbers::Clone | Документация Майкрософт
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
- IDiaEnumLineNumbers::Clone method
ms.assetid: fcd2479a-8ff7-4aba-a737-06123c280d54
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6d9563d950948c7cc6f360af3d5bd62b2cd66e99
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51725113"
---
# <a name="idiaenumlinenumbersclone"></a>IDiaEnumLineNumbers::Clone
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Создает перечислитель с тем же состоянием перечисления, что и текущий перечислитель.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT Clone (   
   IDiaEnumLineNumbers** ppenum  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppenum`  
 [out] Возвращает [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) , содержащий копию перечислителя. Номер строки, числа не дублируются, только перечислитель...  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)




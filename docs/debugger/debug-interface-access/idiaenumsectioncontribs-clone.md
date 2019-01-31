---
title: IDiaEnumSectionContribs::Clone | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::Clone method
ms.assetid: 81d3f3a7-3684-4e5c-b028-29b268684a2c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 89c5c7eef010de75165ac6d28e0690fe2e906d00
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54999162"
---
# <a name="idiaenumsectioncontribsclone"></a>IDiaEnumSectionContribs::Clone
Создает перечислитель с тем же состоянием перечисления, что и текущий перечислитель.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT Clone(   
   IDiaEnumSectionContrib** ppenum  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 ppenum  
 [out] Возвращает [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md) , содержащий копию перечислителя. Раздел, который публикации не дублируются, только перечислитель.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также раздел  
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)
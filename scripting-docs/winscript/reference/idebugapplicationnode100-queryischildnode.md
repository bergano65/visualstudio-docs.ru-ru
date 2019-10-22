---
title: 'IDebugApplicationNode100:: Куерисчилдноде | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNode100::QueryIsChildNode
ms.assetid: 4f36f435-0f34-4f9e-bba3-e75285fd7bbb
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 761b2800415adbcf298eb96f2231a74195b2291c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574746"
---
# <a name="idebugapplicationnode100queryischildnode"></a>IDebugApplicationNode100::QueryIsChildNode
Определяет, принадлежит ли указанный документ одному из дочерних узлов этого узла.  
  
> [!IMPORTANT]
> [Интерфейс IDebugApplicationNode100](../../winscript/reference/idebugapplicationnode100-interface.md) реализуется с помощью PDM v 10.0 и более поздних версий. Обнаружено в activdbg100.h.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT QueryIsChildNode(        [in] IDebugDocument* pSearchKey        );  
```  
  
#### <a name="parameters"></a>Параметры  
 `pSearchKey`  
 Ключ поиска.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugApplicationNode100](../../winscript/reference/idebugapplicationnode100-interface.md)
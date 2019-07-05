---
title: IDebugApplicationNode100::QueryIsChildNode | Microsoft Docs
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
ms.openlocfilehash: 959de620e1e556d92a51dcab0062fa6ff055ec46
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446669"
---
# <a name="idebugapplicationnode100queryischildnode"></a>IDebugApplicationNode100::QueryIsChildNode
Определяет, относится ли указанный документ на один из дочерних узлов данного узла.  
  
> [!IMPORTANT]
> [Интерфейс IDebugApplicationNode100](../../winscript/reference/idebugapplicationnode100-interface.md) является реализуется PDM v10.0 и более поздней версии. Обнаружено в activdbg100.h.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT QueryIsChildNode(        [in] IDebugDocument* pSearchKey        );  
```  
  
#### <a name="parameters"></a>Параметры  
 `pSearchKey`  
 Ключ поиска.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugApplicationNode100](../../winscript/reference/idebugapplicationnode100-interface.md)
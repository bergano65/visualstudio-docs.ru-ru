---
title: Определение типа (Typedef) JsRef | Документы Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 6aafc39f-6b9c-457f-8bf0-48831bffe9b8
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d9d4c478a45f53e83dfa59fdde21cfa4c988c92e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568534"
---
# <a name="jsref-typedef"></a>Определение типа (Typedef) JsRef
Ссылка на объект, относящийся к сборщику мусора Chakra.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
typedef void *JsRef;  
```  
  
## <a name="remarks"></a>Примечания  
 Среда выполнения Chakra будет автоматически отслеживать ссылки JsRef, пока они хранятся в локальных переменных или в параметрах (например, в стеке). Чтобы хранить JsRef где-либо, кроме стека, необходимо вызывать методы JsAddRef и JsRelease, управляющие временем существованием объекта. В противном случае сборщик мусора может освободить объект, даже если он еще используется.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jsrt.h  
  
## <a name="see-also"></a>См. также  
 [Справочник (среда выполнения JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
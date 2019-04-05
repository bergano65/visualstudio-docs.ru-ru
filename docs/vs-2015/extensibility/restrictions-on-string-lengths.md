---
title: Ограничения длины строки | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, restrictions on string lengths
ms.assetid: 877173d2-ca27-43b3-b1f4-8379f7c5e268
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a7abc4290f784808f98b2c5833c896866ab51799
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58980171"
---
# <a name="restrictions-on-string-lengths"></a>Ограничения длины строки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

API подключаемых модулей управления источника ограничивает длину строки, используемые в различных функций.  
  
## <a name="string-length-values"></a>Длина строковых значений  
  
|Константа|Значение|  
|--------------|-----------|  
|`SCC_NAME_LEN`|31|  
|`SCC_AUXLABEL_LEN`|31|  
|`SCC_USER_LEN`|31|  
|`SCC_PRJPATH_LEN`|300|  
  
> [!NOTE]
>  Длина не содержит завершающего `null`. Другие константы с суффиксом «_размер» вместо «_LEN» учитывает пространство для завершающего `null`.  
  
|Константа|Значение|  
|--------------|-----------|  
|SCC_NAME_SIZE|32|  
|SCC_AUXLABEL_SIZE|32|  
|SCC_USER_SIZE|32|  
|SCC_PRJPATH_SIZE|301|  
  
## <a name="see-also"></a>См. также  
 [Подключаемые модули системы управления версиями](../extensibility/source-control-plug-ins.md)

---
title: Предварительные условия для 64-разрядных приложений развертывания | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [Visual Studio], 64-bit
- 64-bit [Visual Studio]
- 64-bit programming [Visual Studio]
- 64-bit applications [Visual Studio]
ms.assetid: 87399e20-5510-41e4-b5b7-4a87c5773f21
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 2ac12f6992e32566e95170410b33e626d0bcfa3a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49286446"
---
# <a name="deploying-prerequisites-for-64-bit-applications"></a>Предварительные условия для развертывания 64-разрядных приложений
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Развертывание приложений ClickOnce поддерживает установку приложений на 64-разрядные платформы. Целевыми платформами являются **x86** для 32-разрядных платформах **x64** для компьютеров, поддерживающих наборы инструкций AMD64 и EM64T, а **Itanium** для 64-разрядного процессора Itanium.  
  
## <a name="prerequisites"></a>Предварительные требования  
 В следующей таблице перечислены распространяемые компоненты, которые можно использовать в качестве необходимых компонентов для установки 64-разрядных приложений.  
  
 Если вы выбрали необходимый компонент, не включающий 64-разрядные элементы, система выдаст предупреждение о том, что выбранные пакеты недоступны для 64-разрядных платформ.  
  
|Распространяемые компоненты|Поддержка x64|Поддержка IA64|  
|---------------------|-----------------|------------------|  
|[!INCLUDE[vsto_runtime](../includes/vsto-runtime-md.md)]|Да|Нет|  
|Библиотеки среды выполнения Visual C++ 2010 (IA64)|Нет|Да|  
|Библиотеки среды выполнения Visual C++ 2010 (x64)|Да|Нет|  
|Microsoft .NET Framework 4 (x86 и x64)|Да||  
|Клиентский профиль Microsoft .NET Framework 4 (x86 и x64)|Да||  
  
## <a name="see-also"></a>См. также  
 [Развертывание приложений, служб и компонентов](../deployment/deploying-applications-services-and-components.md)   
 [Практическое руководство. Установка необходимых компонентов для приложения ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [64-разрядные приложения](http://msdn.microsoft.com/library/fd4026bc-2c3d-4b27-86dc-ec5e96018181)




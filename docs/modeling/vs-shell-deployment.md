---
title: Развертывание VS Shell
ms.date: 11/04/2016
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0e010d2efd8174f2c61d7c97eb63d585f47812ff
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663663"
---
# <a name="vs-shell-deployment"></a>Развертывание VS Shell

Изолированная оболочка позволяет определить, какие функциональные возможности Visual Studio необходимы для взаимодействия с конкретным доменным языком и как это решение должно отображаться. Дополнительные сведения о изолированной оболочке Visual Studio см. [в разделе Настройка изолированной оболочки](https://vspartner.com/pages/vsshells).

Чтобы задать оболочку Visual Studio в качестве цели развертывания, сделайте следующее:

1. В проекте **DslPackage** откройте **source.extension.TT**.

2. В разделе `<SupportedProducts>` вставить:

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   Замените *мисолатедшелл* именем пакета изолированной оболочки.
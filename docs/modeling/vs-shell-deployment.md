---
title: Развертывание VS Shell
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 99ef0124c06cd6f1a4d24e29b2c02cd0b50a37b0
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2020
ms.locfileid: "76115269"
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

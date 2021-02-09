---
title: Развертывание VS Shell
description: Узнайте, как изолированная оболочка позволяет определить, какие функциональные возможности Visual Studio необходимы для взаимодействия с DSL и как это решение должно отображаться.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1293593e71aa57d8e74b9035320b3da5108aba09
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924214"
---
# <a name="vs-shell-deployment"></a>Развертывание VS Shell

Изолированная оболочка позволяет определить, какие функциональные возможности Visual Studio необходимы для взаимодействия с конкретным доменным языком и как это решение должно отображаться. Дополнительные сведения о изолированной оболочке Visual Studio см. [в разделе Настройка изолированной оболочки](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/).

Чтобы задать оболочку Visual Studio в качестве цели развертывания, сделайте следующее:

1. В проекте **DslPackage** откройте **source.extension.TT**.

2. В разделе `<SupportedProducts>` "вставить":

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   Замените *мисолатедшелл* именем пакета изолированной оболочки.
---
title: Развертывание VS Shell
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d8793312e0ed022fc7210508efdf20a81b293f0f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85535854"
---
# <a name="vs-shell-deployment"></a>Развертывание VS Shell

Изолированная оболочка позволяет определить, какие функциональные возможности Visual Studio необходимы для взаимодействия с конкретным доменным языком и как это решение должно отображаться. Дополнительные сведения о изолированной оболочке Visual Studio см. [в разделе Настройка изолированной оболочки](https://docs.microsoft.com/visualstudio/extensibility/customizing-the-isolated-shell).

Чтобы задать оболочку Visual Studio в качестве цели развертывания, сделайте следующее:

1. В проекте **DslPackage** откройте **source.extension.TT**.

2. В разделе `<SupportedProducts>` "вставить":

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   Замените *мисолатедшелл* именем пакета изолированной оболочки.

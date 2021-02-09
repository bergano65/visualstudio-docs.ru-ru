---
title: Развертывание решения Office
description: Решения Office можно развертывать с помощью ClickOnce или установщика Windows. С помощью ClickOnce можно сократить число шагов, необходимых для развертывания решения.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ClickOnce deployment [Office development in Visual Studio], event viewer
- deploying applications [Office development in Visual Studio], event viewer
- Office applications [Office development in Visual Studio], deploying Office solutions
- Office development in Visual Studio, deploying Office solutions
- ClickOnce deployment [Office development in Visual Studio], troubleshooting
- deploying applications [Office development in Visual Studio], Office solutions (2007 system)
- Office development in Visual Studio, troubleshooting
- Office development in Visual Studio, event viewer
- ClickOnce deployment [Office development in Visual Studio], about ClickOnce solution deployments
- Office solutions [Office development in Visual Studio], deploying
- deploying applications [Office development in Visual Studio], troubleshooting
- solutions [Office development in Visual Studio], deploying Office solutions (2007 system)
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 07e4734916f312f40def034a78dd007310e96d9e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888905"
---
# <a name="deploy-an-office-solution"></a>Развертывание решения Office
  Решения Office можно развертывать с помощью ClickOnce или установщика Windows. Использование ClickOnce позволяет сократить число шагов, необходимых для развертывания и обновления решения. При использовании установщика Windows разработчик получает больший контроль над процессом установки решения и над тем, какие именно страницы программы установки отображаются, когда пользователь устанавливает решение.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="deploy-a-solution-by-using-clickonce"></a>Развертывание решения с помощью ClickOnce
 При развертывании решения с помощью ClickOnce оно публикуется в центральном расположении, откуда пользователи могут устанавливать и запускать его. Решение можно обновить без необходимости передачи пользователям новой программы установки.  Этот вариант развертывания проще, но он не позволяет работать с пользовательскими страницами мастера установки. Кроме того, на компьютерах с несколькими пользователями решения должны устанавливаться по несколько раз. См. статью [развертывание решения Office с помощью ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).

## <a name="deploy-a-solution-by-using-windows-installer"></a>Развертывание решения с помощью установщик Windows
 При развертывании решения с помощью установщика Windows программа установки распространяется среди пользователей, а пользователи, в свою очередь, устанавливают решение с помощью этой программы. Программа установки позволяет установить решение сразу для всех пользователей компьютера, а не только для текущего пользователя. Также она дает больший контроль над тем, какие параметры видны пользователям при установке решения. Например, можно показать пользователям лицензионное соглашение или позволить им установить только часть компонентов решения. Однако при обновлении решения необходимо передать пользователям новую программу установки. См. статью [развертывание решения Office с помощью установщик Windows](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md).

## <a name="see-also"></a>См. также раздел
- [Безопасные решения Office](../vsto/securing-office-solutions.md)
- [Развертывание решения Office с помощью ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Развертывание решения Office с помощью установщик Windows](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md)
- [Устранение неполадок развертывания решений Office](../vsto/troubleshooting-office-solution-deployment.md)

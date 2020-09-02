---
title: Общие сведения о модели автоматизации | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e17164976062ec916074c6210be6ae42e8ea1d03
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65699512"
---
# <a name="automation-model-overview"></a>Общие сведения о модели автоматизации
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Модель автоматизации состоит из набора объектов, с которыми можно создать надстройку или расширение Visual Studio. Надстройка — это приложение, которое может управлять средой Visual Studio и автоматизировать общие задачи. Расширение Visual Studio может создавать пользовательские компоненты Visual Studio или добавлять к функциональным возможностям стандартных компонентов, таких как текстовый редактор.  
  
## <a name="objects-in-the-automation-model"></a>Объекты в модели автоматизации  
 Модель автоматизации состоит из связанных групп объектов, которые управляют основными аспектами общей среды. Ниже приведена схема, на которой показан обширный набор объектов, составляющих модель автоматизации.  
  
 ![Таблица объекта анимации Visual Studio](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "всвисуалстудиоаутоматионобжектчарт")  
Объекты автоматизации Visual Studio  
  
 Дополнительные сведения см. [в разделе Расширение среды Visual Studio](https://msdn.microsoft.com/library/4173a963-7ac7-4966-9bb7-e28a9d9f6792).  
  
 Среда предоставляет модель для различных функциональных областей. Например, существует модель кода для различных элементов, которые могут быть найдены в коде. Существует модель документа для различных элементов документа. Одна область, область проекта, является особым интересом к поставщикам VSPackage. Вам, вероятно, потребуется, чтобы новые типы проектов участвовали в модели автоматизации практически так же, как [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] и в [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] модели автоматизации. Этот процесс описан в этой процедуре [для обеспечения автоматизации пакетов VSPackage](../../extensibility/internals/providing-automation-for-vspackages.md).  
  
 Места, где можно расдумать расширение модели автоматизации среды:  
  
- Проект  
  
- Документ  
  
- Код  
  
- Сборка  
  
  Дополнительные сведения об автоматизации см. в разделе [Автоматизация и расширяемость для Visual Studio](https://msdn.microsoft.com/library/f71a2253-3e68-4e5e-9a18-edbba816caf6). Этот документ и содержащиеся в нем документы содержат ссылки на, которые помогут принять решение о том, как следует предоставлять автоматизацию для VSPackage.  
  
## <a name="see-also"></a>См. также:  
 [Практическое руководство. Создание надстройки](https://msdn.microsoft.com/library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)

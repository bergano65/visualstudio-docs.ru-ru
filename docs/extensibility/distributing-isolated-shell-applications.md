---
redirect_url: shell/distributing-isolated-shell-applications
title: "Распространение приложения изолированной оболочки | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c503a985-d67a-4ef8-9123-7744a78f2f17
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 250f1d7769f6035e015eeb7247c439b27f913b78
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="distributing-isolated-shell-applications"></a>Распространение приложения изолированной оболочки
Чтобы создать приложение изолированной оболочки, необходимо установить Visual Studio и пакет SDK для Visual Studio. Для распространения приложения на компьютерах других пользователей или клиентов, необходимо включить специальные распространяемого пакета для изолированной оболочки.  
  
## <a name="prerequisites-for-distributing-isolated-shell-applications"></a>Необходимые условия для распространения приложения изолированной оболочки  
  
|name|Описание:|  
|----------|-----------------|  
|SDK для Visual Studio|Пакет SDK, необходимо иметь для разработки и тестирования расширений [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Также можно использовать пакет SDK для создания собственного экземпляра оболочки Visual Studio изолированной.<br /><br /> Visual Studio является необходимым условием для пакета SDK.|  
|Microsoft Visual Studio Isolated Shell распространяемого пакета|Распространяемый пакет, включить в программу установки, при построении и среду инструментов Visual Studio изолированной оболочки. Распространяемый пакет оболочки изолированного включает .NET Framework 4.5.|  
  
## <a name="creating-an-installation-program-for-the-application"></a>Создание программы установки для приложения  
 Необходимо создать отдельную установку программы для приложения встроенной или изолированной оболочки. Дополнительные сведения см. в разделе [установить приложение изолированной оболочки](../extensibility/installing-an-isolated-shell-application.md).  
  
## <a name="allowing-for-updates-to-your-application"></a>Поддержка обновлений приложения  
 Программе установки необходимо разрешить вероятность того, что приложения будут обновлены, центра обновления Майкрософт или путем обновления вашей компании. Дополнительные сведения об обновлениях см. в разделе [правила обслуживания для приложения изолированной оболочки](../extensibility/servicing-guidelines-for-isolated-shell-applications.md).
---
title: Распространение приложений изолированной оболочки | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c503a985-d67a-4ef8-9123-7744a78f2f17
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bf0d8a4cab8d30a56e84d1a6869c2c842b982aea
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204666"
---
# <a name="distributing-isolated-shell-applications"></a>Распространение приложений изолированной оболочки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Для создания изолированного приложения оболочки необходимо установить Visual Studio и пакет SDK для Visual Studio. Чтобы распространить приложение на компьютеры других пользователей или клиентов, необходимо включить специальный распространяемый пакет для изолированной оболочки.  
  
## <a name="prerequisites-for-distributing-isolated-shell-applications"></a>Необходимые условия для распространения изолированных приложений оболочки  
  
|Имя|Описание|  
|----------|-----------------|  
|SDK для Visual Studio|Пакет SDK необходимо для разработки и тестирования расширений [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Кроме того, с помощью пакета SDK можно создать собственный экземпляр изолированной оболочки Visual Studio.<br /><br /> Visual Studio является необходимым условием для пакета SDK.|  
|Microsoft Visual Studio распространяемый компонент изолированной оболочки|Распространяемый пакет, включенный в программу установки при создании среды инструментов в изолированной оболочке Visual Studio. Распространяемый пакет изолированной оболочки содержит .NET Framework 4,5.|  
  
## <a name="creating-an-installation-program-for-the-application"></a>Создание программы установки для приложения  
 Необходимо создать специальную программу установки для интегрированного или изолированного приложения оболочки. Дополнительные сведения см. в разделе [Установка изолированной оболочки приложения](../extensibility/installing-an-isolated-shell-application.md).  
  
## <a name="allowing-for-updates-to-your-application"></a>Разрешение обновлений для приложения  
 Программа установки должна допускать возможность обновления приложения либо обновлениями Майкрософт, либо обновлениями вашей компании. Дополнительные сведения об обновлениях см. в разделе [рекомендации по обслуживанию изолированных приложений оболочки](../extensibility/servicing-guidelines-for-isolated-shell-applications.md).

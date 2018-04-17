---
title: 'Как: Установка местоположения файла настраиваемого журнала для ошибок развертывания ClickOnce | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
- ClickOnce deployment, error logging
ms.assetid: 77424414-7f0e-4b99-94bb-ea130de92d09
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: a54946f5750e901c937dd91772eb7d7ecb740e48
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-set-a-custom-log-file-location-for-clickonce-deployment-errors"></a>Практическое руководство. Задание местоположения файла настраиваемого журнала для ошибок развертывания ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] обслуживает файлы журналов активации для всех развертываний. Этих журналах содержатся все ошибки, относящиеся к установке и инициализации [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] развертывания. По умолчанию [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] создается один файл журнала для активации каждого развертывания. Он хранит файлы журнала в папке временных файлов Интернета. Файл журнала для развертывания отображается для пользователя, когда происходит сбой активации, и пользователь нажимает кнопку **сведений** в диалоговом окне возникшей ошибки.  
  
 Это поведение можно изменить для конкретного клиента с помощью редактора реестра (**regedit.exe**), чтобы задать путь к файлу пользовательского журнала. В этом случае [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] регистрирует успешные и неудачные для всех развертываний в одном файле.  
  
> [!CAUTION]
>  Неправильное использование редактора реестра может привести к серьезным проблемам, которые могут потребовать переустановки операционной системы. Используйте редактор реестра на свой страх и риск.  
  
> [!NOTE]
>  Необходимо усечь или удалить файл журнала периодически, чтобы предотвратить его становится слишком большим.  
  
 Следующая процедура описывает, как для задания местоположения файла настраиваемого журнала для отдельного клиента.  
  
### <a name="to-set-a-custom-log-file-location"></a>Для задания местоположения файла настраиваемого журнала  
  
1.  Откройте **Regedit.exe**.  
  
2.  Перейдите к узлу `HKCU\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`.  
  
3.  Задайте строковое значение `LogFilePath` содержит полный путь и имя файла настраиваемого журнала расположения.  
  
     Должен находиться в каталоге, к которой пользователь имеет доступ на запись. Например, в Windows Vista, создайте следующую структуру папок и задать `LogFilePath` для C:\Users\\< имя_пользователя\>\Documents\Logs\ClickOnce\installation.log.  
  
## <a name="see-also"></a>См. также  
 [Устранение неполадок развертывания ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)
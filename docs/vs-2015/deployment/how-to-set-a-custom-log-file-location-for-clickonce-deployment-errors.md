---
title: Практическое руководство. Задание местоположения файла настраиваемого журнала для ошибок развертывания ClickOnce | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7a1b7c93e4b30bbfd373a5fad9d7001452d4f587
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63403550"
---
# <a name="how-to-set-a-custom-log-file-location-for-clickonce-deployment-errors"></a>Практическое руководство. Задание местоположения файла настраиваемого журнала для ошибок развертывания ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] хранит файлы журналов активации для всех развертываний. Эти журналы документировать все ошибки, относящиеся к установке и инициализации [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] развертывания. По умолчанию [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] создает один файл журнала для активации каждого развертывания. Он сохраняет эти файлы журнала в папке временных файлов Интернета. Файл журнала для развертывания отображается для пользователя, когда происходит сбой активации, и пользователь нажимает кнопку **сведения** в диалоговом окне возникшей ошибки.  
  
 Это поведение можно изменить для конкретного клиента с помощью редактора реестра (**regedit.exe**) чтобы задать путь к файлу пользовательского журнала. В этом случае [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] регистрирует успешные и неудачные для всех развертываний в одном файле.  
  
> [!CAUTION]
> Неправильное использование редактора реестра может привести к серьезным проблемам, которые могут потребовать переустановки операционной системы. Используйте редактор реестра на свой страх и риск.  
  
> [!NOTE]
> Необходимо будет выполнено усечение или удаление файла журнала, время от времени, чтобы предотвратить ее становится слишком большим.  
  
 Следующая процедура описывает задание местоположения файла настраиваемого журнала для отдельного клиента.  
  
### <a name="to-set-a-custom-log-file-location"></a>Для задания местоположения файла настраиваемого журнала  
  
1. Откройте **Regedit.exe**.  
  
2. Перейдите к узлу `HKCU\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`.  
  
3. Задайте строковое значение `LogFilePath` полный путь и имя файла настраиваемого журнала расположения.  
  
     Это расположение должно быть в каталоге, к которому пользователь имеет доступ на запись. Например, в Windows Vista, создайте следующую структуру папок и задать `LogFilePath` для C:\Users\\< имя пользователя\>\Documents\Logs\ClickOnce\installation.log.  
  
## <a name="see-also"></a>См. также  
 [Устранение неполадок развертывания ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)

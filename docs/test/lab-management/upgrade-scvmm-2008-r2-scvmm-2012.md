---
title: "Обновление диспетчера SCVMM 2008 R2 до версии SCVMM 2012 | Документы Майкрософт"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Upgrade SCVMM 2008 R2 to SCVMM 2012, test lab
ms.assetid: 5be92444-c701-43c7-8b2a-77df8e02bc27
caps.latest.revision: "56"
ms.author: douge
manager: douge
ms.openlocfilehash: 281cf7b876c67d3c9eefa0aa7a56621de1ea791c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="upgrade-scvmm-2008-r2-to-scvmm-2012"></a>Обновление диспетчера SCVMM 2008 R2 до версии SCVMM 2012

Lab Management для Team Foundation Server поддерживает SCVMM 2008 R2 и SCVMM 2012. Если вы обновляете Team Foundation Server 2013 до Team Foundation Server 2015 и планируете обновить SCVMM 2008 R2 до SCVMM 2012, рекомендуется обновиться до SCVMM 2012 после завершения обновления до Team Foundation Server 2015. Этот раздел описывает обновление SCVMM 2008 R2 до SCVMM 2012 при использовании Lab Management в Team Foundation Server 2015.
Lab Management **не** поддерживает SCVMM 2016. 

**Важно!** При обновлении SCVMM отдельные действия приведут к простою Team Foundation Server в течение некоторого времени. Эти действия указаны ниже.

## <a name="upgrading-to-scvmm-2012"></a>Обновление до SCVMM 2012

1. Используйте установщик SCVMM 2012 для обновления программного обеспечения SCVMM 2008 R2 Server до SCVMM 2012 Server.

1. Обновите агенты SCVMM в узлах и общих папках библиотеки.

1. С помощью консоли администрирования SCVMM убедитесь в функционировании всех компонентов SCVMM.

1. Установите на всех компьютерах уровня приложений сервера Team Foundation Server консоль администрирования SCVMM 2012.

1. Используйте команду **iisreset**, чтобы перезапустить веб-службу Team Foundation Server. Затем перезапустите агент заданий Team Foundation Server.

   **Внимание!** Это действие приведет к нарушению работы служб в Team Foundation Server.

1. Обновите данные и шаблоны во всех базах данных коллекции проектов для обеспечения совместимости с SCVM. 
   2012.

   Откройте командную строку с повышенными привилегиями на сервере Team Foundation Server и введите следующую команду:

   **C:\\Program Files\\Microsoft Team Foundation Server 14.0\\средства\> tfsconfig lab /upgradeSCVMM /collectionName:\***

   При вводе команды **upgradeSCVMM** программное обеспечение Team Foundation Server создаст на сервере SCVMM новый объект шаблона для каждого командного проекта, использующего этот шаблон. Это гарантирует обновление шаблонов для обеспечения совместимости с SCVMM 2012 без потери данных. Однако при создании новых шаблонов к имени шаблона добавляется имя командного проекта.

   **Внимание!**  
   Если длина имени нового шаблона больше 64 символов, произойдет сбой SCVMM. Чтобы устранить эту ошибку, необходимо присвоить шаблону более короткое имя. В случае появления любых других ошибок или предупреждений при выполнении этой команды для их устранения обратитесь к следующему разделу. Если никаких ошибок и предупреждений не появляется, обновление выполнено и можно начать использовать среды SCVMM с Lab Management.

## <a name="resolving-errors-and-warnings-when-using-the-upgradescvmm-command"></a>Устранение ошибок и предупреждений при использовании команды upgradeSCVMM

После ввода команды **upgradeSCVMM** нужно устранить все появившиеся ошибки и предупреждения, а затем снова выполнить эту команду, чтобы начать работу с Lab Management. Команда **upgradeSCVMM** создает файл журнала со сведениями о любых появившихся ошибках и предупреждениях. Расположение этого файла отображается при выполнении команды **upgradeSCVMM**.

**Сбой SCVMM.** В случае появления ошибки, связанной со сбоем SCVMM, для получения дополнительных сведений о ней используйте журнал заданий SCVMM. После устранения ошибки в SCVMM снова выполните команду **upgradeSCVMM**.

## <a name="see-also"></a>См. также

* [Изменение существующих конфигураций Lab Management](https://msdn.microsoft.com/library/ee704508%28v=vs.140%29.aspx)

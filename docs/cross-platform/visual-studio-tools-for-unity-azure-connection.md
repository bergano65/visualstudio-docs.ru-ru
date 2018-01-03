---
title: "Инструменты Visual Studio для Unity. Пошаговое руководство по подключению в Azure | Документы Майкрософт"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 516A8FB2-8DFF-4BAB-8116-FDCD1C228DB3
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: cb2ce447f21231b98d6464824ba7d088fee16cce
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="test-the-client-connection"></a>Тестирование клиентских подключений

Теперь, когда создан экземпляр AzureMobileServiceClient, пора протестировать клиентское подключение.

## <a name="create-the-testclientconnection-script"></a>Создание скрипта TestClientConnection

1. В Unity в папке **Scripts** создайте скрипт C# с именем **TestClientConnection**.

2. Откройте скрипт в Visual Studio, удалите весь код шаблона и добавьте следующий код:

  ```csharp
  using System.Collections.Generic;
  using UnityEngine;
  using System.Threading.Tasks;
  using System;
  using System.Linq;
  using Microsoft.WindowsAzure.MobileServices;

  public class TestClientConnection : MonoBehaviour
  {
      void Start()
      {
          Task.Run(TestTableConnection);
      }

      private async Task TestTableConnection()
      {
          var table = AzureMobileServiceClient.Client.GetTable<CrashInfo>();

          Debug.Log("Testing ToListAsync...");
          await TestToListAsync(table);

          Debug.Log("Testing InsertAsync...");
          await TestInsertAsync(table);

          Debug.Log("Testing DeleteAsync...");
          await TestDeleteAsync(table);

          Debug.Log("All testing complete.");
      }

      private async Task TestInsertAsync(IMobileServiceTable<CrashInfo> table)
      {
          try
          {
              var allEntries = await TestToListAsync(table);
              var initialCount = allEntries.Count();

              await table.InsertAsync(new CrashInfo { X = 1, Y = 2, Z = 3 });

              allEntries = await TestToListAsync(table);
              var newCount = allEntries.Count();

              Debug.Assert(newCount == initialCount + 1, "InsertAsync failed!");
          }
          catch (Exception)
          {
              throw;
          }
      }

      private async Task<List<CrashInfo>> TestToListAsync(IMobileServiceTable<CrashInfo> table)
      {
          try
          {
              var allEntries = await table.ToListAsync();
              Debug.Assert(allEntries != null, "ToListAsync failed!");
              return allEntries;
          }
          catch (Exception)
          {

              throw;
          }
      }

      private async Task TestDeleteAsync(IMobileServiceTable<CrashInfo> table)
      {
          var allEntries = await TestToListAsync(table);

          foreach (var item in allEntries)
          {
              try
              {
                  await table.DeleteAsync(item);
              }
              catch (Exception)
              {
                  throw;
              }
          }

          allEntries = await TestToListAsync(table);

          Debug.Assert(allEntries.Count() == 0, "DeleteAsync failed!");
      }
  }
  ```

3. В Unity в меню **GameObject** выберите пункты **GameObject > Create Empty** (GameObject > Создать пустой), чтобы создать пустой объект GameObject в сцене Unity. Переименуйте объект в **TestClientConnection**.

4. **Перетащите** скрипт TestClientConnection из окна **Project** (Проект) в Unity в объект GameObject с именем TestClientConnection в окне **Hierarchy** (Иерархия).

5. В меню Unity выберите пункты **File > Save Scene as...** (Файл > Сохранить сцену как...). Присвойте сцене имя **Client Connection Test** и нажмите кнопку **Save** (Сохранить).

5. В Unity нажмите кнопку **Play** (Воспроизвести) и проследите за результатом в окне консоли. Убедитесь в том, что ни одно из утверждений не завершилось сбоем.

6. На портале Azure откройте простую таблицу CrashInfo. Теперь в ней должна быть запись с координатами **X,Y,Z** **(1, 2, 3)** и значением **true** в столбце **deleted**. При каждом выполнении теста в таблицу должна добавляться новая запись с теми же значениями, но уникальным идентификатором.

  ![Запись в простой таблице](media/vstu_azure-test-client-connection-image1.png)

## <a name="next-step"></a>Дальнейшие действия
* [Импорт ресурсов образца игры](visual-studio-tools-for-unity-azure-game-assets.md)

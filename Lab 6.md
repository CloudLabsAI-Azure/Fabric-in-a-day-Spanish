# 目录 {#目录 .TOC-Heading}

简介 

- Lakehouse 

    - 任务 1：使用 SQL 查询数据

    - 任务 2：可视化 T-SQL 结果

    - 任务 3：创建视觉对象查询

    - 任务 4：可视化查询结果

    - 任务 5：创建关系 

    - 任务 6：创建度量 

    - 任务 7：可选部分 - 创建关系

    - 任务 8：可选部分 - 创建度量

参考  

# 简介

我们已将来自不同来源的数据引入到
Lakehouse。在本实验中，您将使用数据模型。我们通常在 Power BI Desktop
中执行建模活动，例如创建关系、添加度量等。接下来我们将学习如何在该服务中执行这些建模活动。

本实验结束后，您将学会：

-   如何探索 Lakehouse

-   如何探索 Lakehouse 的 SQL 视图

-   如何探索 Lakehouse 中的数据建模

# Lakehouse

### 任务 1：使用 SQL 查询数据

1.  让我们导航回到您在实验 2 任务 8 中创建的 Fabric 工作区
    **FAIAD\_\<username\>**。

2.  导航回到 **Data Factory 屏幕**。

3.  您将看到三种类型的 lh_FAIAD - 语义模型、SQL 终结点和
    Lakehouse。我们在之前的实验中探索了 Lakehouse 选项。选择 **lh_FAIAD
    SQL 分析终结点**选项来探索 SQL 选项。您将导航到 Explorer 的 **SQL
    视图**。

如果您想在创建数据模型之前探索数据，可以使用 SQL
执行此操作。我们来看一下使用 SQL
的两个选项，第一个选项适合开发人员，第二个选项适合分析师。

假设您想要使用 SQL 快速找出供应商销售的单位数量。我们有两种选项，编写
SQL 语句或使用视觉对象创建 SQL 语句。

请注意，在左侧面板上，您可以查看表。展开表后，可以查看组成表的列。此外，还有创建
SQL 视图、函数和存储过程的选项。如果您具备 SQL
背景知识，请随意探索这些选项。我们来尝试编写一个简单的 SQL 查询。

4.  从**顶部菜单**选择**新建 SQL
    查询**，或从**左下角面板**选择**查询**。您将导航到 SQL 查询视图。


5.  将**以下 SQL
    查询**粘贴到**查询窗口**中。此查询将按供应商名称返回单位数量。它将
    Sales 表与 Product 和 Supplier 表联接起来以实现此目的。
```
SELECT su.Supplier_Name, SUM(Quantity) as Units

FROM dbo.Sales s

JOIN dbo.Product p on p.StockItemID = s.StockItemID

JOIN dbo.Supplier su on su.SupplierID = p.SupplierID
```

按 su.Supplier_Name 分组

6.  点击 **Run** 查看结果。

7.  请注意，可以通过选择**另存为视图**来将此查询另存为视图。

8.  在**左侧** **Explorer**
    面板上的**查询**部分，请注意此查询保存在**我的查询**下，为 **SQL
    query
    1**。这里提供一个选项用于重命名并保存该查询以供将来使用。还有一个选项用于使用**共享查询**文件夹查看与您共享的查询。

###  任务 2：可视化 T-SQL 结果

1.  我们还可以可视化该查询的结果。在查询窗格中**突出显示查询**，然后选择**结果窗格**，然后选择**可视化结果**。

2.  可视化结果对话框随即打开。选择**继续**。

3.  熟悉的报表视图对话框打开。在**数据窗格**中，展开 **SQL query 1**。

4.  选择 **Supplier_Name** 和 **Units
    字段**。默认情况下会创建表视觉对象。

5.  从**可视化**部分，选择**堆积柱形图**以更改视觉对象类型。

6.  根据需要对视觉对象**调整大小**。\
    \
    **注意**：请注意，可用于对 Power BI
    报表中的视觉对象设置格式的所有选项也可在此处使用。

7.  选择右下角的**另存为报表**。

8.  "保存报表"对话框随即打开。在**为报表输入名称文本框**中，输入 **Units
    by Supplier**。

9.  确保将目标工作区设置为您的 Fabric 工作区 **FAIAD\<username\>**

10. 选择**保存**。

### 任务 3：创建视觉对象查询

您将导航回到 **SQL 分析终结点视图**。如果您不熟悉
SQL，可以使用视觉对象查询执行类似的查询。

1.  在顶部菜单中，选择**新建视觉对象查询**。视觉对象查询窗格随即打开。

2.  从 **Explorer** 窗格中，将 **Sales、Product 和 Supplier**
    表拖至视觉对象查询窗格。

3.  选择 **Sales** 表后，从视觉对象查询窗格菜单中，选择**组合 -\>
    合并查询**。

4.  合并对话框随即打开。从**用于合并的右表下拉菜单**中，选择
    **Product**。

5.  从 **Sales** 和 **Product** 表中，选择 **StockItemID**。这将合并
    Product 和 Sales 表。

6.  在**联接种类**中，选择**左外**。

7.  选择**确定**。

8.  在**结果**窗格中，点击 **Product** 列旁边的**双箭头**。

9.  对话框随即打开，从对话框中选择 **SupplierID**。

10. 选择**确定**。注意，在 **Sales**
    表中创建了**合并查询**和**展开的产品**步骤。

11. 我们按同样的步骤来合并 Supplier 表。在 **Sales**
    表中，选择**"+"**（位于展开的产品之后）以添加新步骤。对话框随即打开。

12. 选择**组合 -\> 合并查询**。

13. 合并对话框随即打开。从**用于合并的右表下拉菜单**中，选择
    **Supplier**。

14. 从 **Sales** 和 **Supplier** 表中，选择 **SupplierID**。这将合并
    Supplier 和 Sales 表。

15. 在**联接种类**中，选择**左外**。

16. 选择**确定**。

17. 在**结果**窗格中，点击 **Supplier** 列旁边的**双箭头**。

18. 对话框随即打开，从对话框中选择 **Supplier_Name**。

19. 选择**确定**。请注意，在 Sales
    表中，添加了**合并查询**，并**记录了所有步骤**。\
    \
    **注意：** 参考任务 4 下的第一个屏幕截图。

### 任务 4：可视化查询结果

1.  现在我们的查询已经就绪，我们来查看结果。从结果窗格中选择**可视化结果**。

2.  可视化结果对话框随即打开。从右侧的**数据**窗格中，选择
    **Supplier_Name** 和 **Quantity** 字段。

3.  在"视觉对象"窗格中，选择**表视觉对象**，以表的形式查看结果。请注意，结果类似于之前的
    SQL
    查询结果。您可以选择保存此报表。由于我们之前保存了类似的报表，因此我们将选择**取消**。

### 任务 5：创建关系

现在我们准备生成模型、生成表之间的关系并创建度量。

1.  在**左侧面板底部**选择**模型**。您会注意到，中间窗格类似于我们在
    Power BI Desktop 中看到的模型视图。

2.  根据需要对表**调整大小和重新排列**。

3.  我们在 Sales 和 Reseller 表之间创建关系。从 **Sales** 表中选择
    **ResellerID**，并将其拖至 **Reseller** 表的 **ResellerID** 中。

4.  "新关系"对话框随即打开。确保 **Table 1** 是 **Sales**，**列**是
    **ResellerID。**

5.  确保 **Table 2** 是 **Reseller**，**列**是 **ResellerID。**

6.  确保**基数**为**多对一 (\*:1)**。

7.  确保**交叉筛选器方向**为 **Single**。

8.  选择 **Ok**。

9.  同样在 Sales 和 Date 表之间创建关系。从 **Sales** 表中选择
    **InvoiceDate**，并将其拖至 **Date** 表的 **Date** 中。

10. "新关系"对话框随即打开。确保 **Table 1** 是 **Sales**，**列**是
    **InvoiceDate。**

11. 确保 **Table 2** 是 **Date**，**列**是 **Date。**

12. 确保**基数**为**多对一 (\*:1)**。

13. 确保**交叉筛选器方向**为 **Single**。

14. 选择 **Ok**。

**检查点：** 您的模型应在 Sales 和 Reseller 表以及 Sales 和 Date
表之间建立两种关系，如下面的屏幕截图所示：

由于时间原因，我们不会创建所有关系。如果时间允许，实验结束后，您可以完成可选部分。可选部分将逐步介绍创建其余关系的步骤。

### 任务 6：创建度量

我们添加一些创建销售仪表板时所需的度量。

1.  从模型视图中选择 **Sales 表**。我们想要将度量添加到 Sales 表中。

2.  从顶部菜单中，选择**主页 -\> 新建度值**。请注意，编辑栏已显示。

3.  在**编辑栏**中输入 **Sales = SUM(Sales\[Sales_Amount\])**。

4.  点击编辑栏左侧的**复选标记**，或点击 **Enter** 按钮。

5.  在右侧的"属性"面板中，展开**格式化**部分。

6.  从**格式**下拉菜单中，选择**货币**。

7.  将**小数位数**设置为 **0**。

8.  从顶部菜单中选择 **Sales 表**后，选择**主页 -\>
    新建度量值**。请注意，编辑栏已显示。

9.  在**编辑栏**中输入 **Units = SUM(Sales\[Quantity\])**。

10. 点击编辑栏左侧的**复选标记**，或点击 **Enter** 按钮。

11. 在右侧的"属性"面板中，展开**格式化**部分（加载"属性"面板可能需要一些时间）。

12. 从**格式**下拉菜单中，选择**整数**。

13. 将**千位分隔符**设置为**是**。

14. 从顶部菜单中选择 **Sales 表**后，选择**主页 -\>
    新建度量值**。请注意，编辑栏已显示。

15. 在**编辑栏**中输入 **Orders = DISTINCTCOUNT(Sales\[InvoiceID\])**。

16. 点击编辑栏左侧的**复选标记**，或点击 **Enter** 按钮。

17. 在右侧的"属性"面板中，展开**格式化**部分。

18. 从**格式**下拉菜单中，选择**整数**。

19. 将**千位分隔符**设置为**是**。

同样由于时间原因，我们不会创建所有度量。如果时间允许，实验结束后，您可以完成可选部分。可选部分将逐步介绍创建其余度量的步骤。

我们已经创建了数据模型，下一步是创建报表。我们将在下一个实验中执行此任务。

### 任务 7：可选部分 - 创建关系

我们来添加其余的关系。

1.  在 **Sales** 表和 **Product** 表之间创建**多对一**关系。从 **Sales**
    表中选择 **StockItemID**，从 **Product** 表中选择 **StockItemID**。

2.  同样，在 **Sales** 和 **People** 之间创建**多对一**关系。从
    **Sales** 中选择 **SalespersonPersonID**，从 **People** 中选择
    **PersonID**。

**检查点：** 您的模型应类似于下面的屏幕截图所示。

3.  我们接下来在 Product 和 Supplier 之间创建关系。从 **Product**
    表中选择 **SupplierID**，并将其拖至 **Supplier** 表的 **SupplierID**
    中。

4.  "新关系"对话框随即打开。确保 **Table 1** 是 **Product**，**列**是
    **SupplierID。**

5.  确保 **Table 2** 是 **Supplier**，**列**是 **SupplierID。**

6.  确保**基数**为**多对一 (\*:1)**。

7.  确保**交叉筛选器方向**为**两者**。

8.  选择 **Ok**。

9.  同样，在 **Product_Details** 和 **Product**
    之间创建**多对一**关系，**交叉筛选器方向**为**两者**。从
    **Product_Details** 中选择 **StockItemID**，从 **Product** 中选择
    **StockItemID**。

10. 我们接下来在 Reseller 和 Geo 之间创建关系。从 **Reseller** 表中选择
    **PostalCityID**，并将其拖至 **Geo** 表中的 **CityID**。

11. "新关系"对话框随即打开。确保 **Table 1** 是 **Reseller**，**列**是
    **PostalCityID。**

12. 确保 **Table 2** 是 **Geo**，**列**是 **CityID。**

13. 确保**基数**为**多对一 (\*:1)**。

14. 确保**交叉筛选器方向**为**两者**。

15. 选择 **Ok**。

16. 我们接下来在 Customer 和 Reseller 之间创建关系。从 **Customer**
    表中选择 **ResellerID**，并将其拖至 **Reseller** 表的 **ResellerID**
    中。

17. "新关系"对话框随即打开。确保 **Table 1** 是 **Customer**，**列**是
    **ResellerID。**

18. 确保 **Table 2** 是 **Reseller**，**列**是 **ResellerID。**

19. 确保**基数**为**多对一 (\*:1)**。

20. 确保**交叉筛选器方向**为 **Single**。

21. 选择 **Ok**。

**检查点：** 您的模型应类似于下面的屏幕截图所示。

22. 我们接下来在 PO 和 Date 之间创建关系。从 **PO** 表中选择
    **Order_Date**，并将其拖至 **Date** 表中的 **Date**。

23. "新关系"对话框随即打开。确保 **Table 1** 是 **PO**，**列**是
    **Order_Date。**

24. 确保 **Table 2** 是 **Date**，**列**是 **Date。**

25. 确保**基数**为**多对一 (\*:1)**。

26. 确保**交叉筛选器方向**为 **Single**。

27. 选择 **Ok**。

28. 同样，在 **PO** 和 **Product** 之间创建**多对一**关系。从 **PO**
    中选择 **StockItemID**，从 **Product** 中选择 **StockItemID**。

29. 同样，在 **PO** 和 **People** 之间创建**多对一**关系。从 **PO**
    中选择 **ContactPersonID**，从 **People** 中选择 **PersonID**。

我们已经创建了所有关系。

**检查点：** 您的模型应类似于下面的屏幕截图所示。

### 任务 8：可选部分 - 创建度量

我们来添加其余的度量。

1.  在编辑栏中输入 **Avg Order = DIVIDE(\[Sales\], \[Orders\])**。

2.  点击编辑栏的**复选标记**，或点击 Enter 按钮。

3.  保存度量后，请注意顶部菜单上的"度量工具"选项。点击**度量工具**。

4.  在"格式"下拉菜单中，点击**货币**。

5.  按照相似的步骤添加以下度量：

    a.  **GM = SUM(Sales\[Line_Profit\])**，格式设置为**货币，小数点后 2
        位**

    b.  **GM% = DIVIDE(\[GM\],
        \[Sales\])**，格式设置为**百分比，小数点后 2 位**

    c.  **No of Customers = COUNTROWS(Customer)**，格式设置为**整数**

# 参考

Fabric Analyst in a Day (FAIAD) 介绍了 Microsoft Fabric
中提供的一些主要功能。在服务菜单中，"帮助
(?)"部分包含指向一些优质资源的链接。

以下更多参考资源可帮助您进行与 Microsoft Fabric 相关的后续步骤。

-   请参阅博客文章以阅读完整的 [Microsoft Fabric GA
    公告](https://aka.ms/Fabric-Hero-Blog-Ignite23)

-   通过[引导式教程](https://aka.ms/Fabric-GuidedTour)探索 Fabric

-   注册 [Microsoft Fabric 免费试用版](https://aka.ms/try-fabric)

-   访问 [Microsoft Fabric 网站](https://aka.ms/microsoft-fabric)

-   通过探索 [Fabric 学习模块](https://aka.ms/learn-fabric)学习新技能

-   探索 [Fabric 技术文档](https://aka.ms/fabric-docs)

-   阅读[有关 Fabric
    入门指南的免费电子书](https://aka.ms/fabric-get-started-ebook)

-   加入 [Fabric
    社区](https://aka.ms/fabric-community)发布问题、分享反馈并向他人学习

阅读更多深度 Fabric 体验公告博客：

-   [Fabric 中的 Data Factory
    体验博客](https://aka.ms/Fabric-Data-Factory-Blog) 

-   [Fabric 中的 Synapse Data Engineering
    体验博客](https://aka.ms/Fabric-DE-Blog) 

-   [Fabric 中的 Synapse Data Science
    体验博客](https://aka.ms/Fabric-DS-Blog) 

-   [Fabric 中的 Synapse Data Warehousing
    体验博客](https://aka.ms/Fabric-DW-Blog) 

-   [Fabric 中的 Synapse Real-Time Analytics
    体验博客](https://aka.ms/Fabric-RTA-Blog)

-   [Power BI 公告博客](https://aka.ms/Fabric-PBI-Blog)

-   [Fabric 中的 Data Activator 博客](https://aka.ms/Fabric-DA-Blog) 

-   [Fabric 中的管理和治理博客](https://aka.ms/Fabric-Admin-Gov-Blog)

-   [Fabric 中的 OneLake 博客](https://aka.ms/Fabric-OneLake-Blog)

-   [Dataverse 和 Microsoft Fabric
    集成博客](https://aka.ms/Dataverse-Fabric-Blog)

© 2023 Microsoft Corporation.保留所有权利。

使用此演示/实验即表示您已同意以下条款：

本演示/实验中的技术/功能由 Microsoft Corporation
出于获取反馈和提供学习体验的目的提供。只能将本演示/实验用于评估这些技术特性和功能以及向
Microsoft
提供反馈。不得用于任何其他用途。不得对此演示/实验或其任何部分进行修改、复制、分发、传送、显示、执行、复制、公布、许可、转让、销售或基于以上内容创建衍生作品。

严禁将本演示/实验（或其任何部分）复制到任何其他服务器或位置以便进一步复制或再分发。

本演示/实验出于上述目的，在不涉及复杂设置或安装操作的模拟环境中提供特定软件技术/产品特性和功能，包括潜在的新功能和概念。本演示/实验中展示的技术/概念可能不是完整的功能，可能会以不同于最终版本的工作方式工作。我们也可能不会发布此类功能或概念的最终版本。在物理环境中使用此类特性和功能的体验可能也有所不同。

**反馈**。如您针对本演示/实验中所述的技术特性、功能和/或概念向
Microsoft 提供反馈，则意味着您向 Microsoft
无偿提供以任何方式、出于任何目的使用和分享您的反馈并将其商业化的权利。您同样无偿为第三方提供其产品、技术和服务使用或配合使用包含此反馈的
Microsoft
软件或服务的任何特定部分所需的任何专利权。如果根据某项许可的规定，Microsoft
由于在其软件或文档中包含了您的反馈需要向第三方授予该软件或文档的许可，请不要提供这样的反馈。这些权利在本协议终止后继续有效。

对于本演示/实验，Microsoft Corporation
不提供任何明示、暗示或法定的保证和条件，包括有关适销性、针对特定目的的适用性、所有权和不侵权的所有保证和条件。对于使用本演示/实验产生的结果或输出内容的准确性，或者出于任何目的包含本演示/实验中的信息的适用性，Microsoft
不做任何保证或陈述。

**免责声明**

本演示/实验仅包含 Microsoft Power BI
的部分新功能和增强功能。在产品的后续版本中，部分功能可能有所更改。在本演示/实验中，可了解部分新功能，但并非全部新功能。

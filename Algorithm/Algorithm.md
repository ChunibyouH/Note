# 算法设计

1. 问题建模
2. 选择什么算法？如何描述这个算法？
3. 这个方法是否对所有实例都得到最优解？如何证明
4. 如果不是，能否找到反例？

总结

- 建模：对输入参数和解给出形式化或半形式化的描述

- 设计算法：

  采用什么算法设计技术

  **正确性**是否对所有的实例都得到正确的解

- 分析算法**效率**

问题及实例

- 问题

  需要回答的一般性提问，通常含若干参数

- 问题描述

  定义问题参数（集合、变量、函数、序列等）

  说明每个参数的取值范围及参数间的关系

  定义问题的解

  说明解满足的条件（优化目标或约束条件）

- 问题的实例

  参数的一组赋值可得到问题的一个实例

<table style="width: 1000px" border="0" cellspacing="0" cellpadding="0">
  <tbody>
    <tr>
      <td colspan="9" nowrap="nowrap" width="1000">
        <p align="center">各种常用排序算法</p>
      </td>
    </tr>
    <tr>
      <td rowspan="2" nowrap="nowrap" width="55">
        <p align="center">类别</p>
      </td>
      <td rowspan="2" nowrap="nowrap" width="60">
        <p align="center">排序方法</p>
      </td>
      <td colspan="3" nowrap="nowrap" width="250">
        <p align="center">时间复杂度</p>
      </td>
      <td nowrap="nowrap" width="104">
        <p>空间复杂度</p>
      </td>
      <td nowrap="nowrap" width="48">
        <p align="center">稳定性</p>
      </td>
      <td nowrap="nowrap" width="48">
        <p>复杂性</p>
      </td>
      <td width="377">
        <p>特点</p>
      </td>
    </tr>
    <tr>
      <td nowrap="nowrap" width="80">
        <p>最好</p>
      </td>
      <td nowrap="nowrap" width="80">
        <p>平均</p>
      </td>
      <td nowrap="nowrap" width="80">
        <p>最坏</p>
      </td>
      <td nowrap="nowrap" width="74">
        <p>辅助存储</p>
      </td>
      <td nowrap="nowrap" width="48">
        <p align="center">&nbsp;</p>
      </td>
      <td nowrap="nowrap" width="48">
        <p>简单</p>
      </td>
      <td nowrap="nowrap" width="377">
        <p>&nbsp;</p>
      </td>
    </tr>
    <tr>
      <td rowspan="2" nowrap="nowrap" width="55">
        <p align="center">插入</p>
        <p align="center">排序</p>
      </td>
      <td nowrap="nowrap" width="60">
        <p>直接插入</p>
      </td>
      <td nowrap="nowrap" width="66">
        <p>O(N)</p>
      </td>
      <td nowrap="nowrap" width="66">
        <p>O(N<sup>2</sup>)</p>
      </td>
      <td nowrap="nowrap" width="66">
        <p>O(N<sup>2</sup>)</p>
      </td>
      <td nowrap="nowrap" width="84">
        <p>O(1)</p>
      </td>
      <td nowrap="nowrap" width="48">
        <p>稳定</p>
      </td>
      <td nowrap="nowrap" width="48">
        <p>简单&nbsp;</p>
      </td>
      <td nowrap="nowrap" width="377">
        <p>&nbsp;</p>
      </td>
    </tr>
    <tr>
      <td nowrap="nowrap" width="60">
        <p>希尔排序</p>
      </td>
      <td nowrap="nowrap" width="66">
        <p>O(N)</p>
      </td>
      <td nowrap="nowrap" width="66">
        <p>O(N<sup>1.3</sup>)</p>
      </td>
      <td nowrap="nowrap" width="66">
        <p>O(N<sup>2</sup>)</p>
      </td>
      <td nowrap="nowrap" width="84">
        <p>O(1)</p>
      </td>
      <td nowrap="nowrap" width="48">
        <p>不稳定</p>
      </td>
      <td nowrap="nowrap" width="48">
        <p>复杂</p>
      </td>
      <td nowrap="nowrap" width="377">
        <p>&nbsp;</p>
      </td>
    </tr>
    <tr>
      <td rowspan="2" nowrap="nowrap" width="55">
        <p align="center">选择</p>
        <p align="center">排序</p>
      </td>
      <td nowrap="nowrap" width="60">
        <p>直接选择</p>
      </td>
      <td nowrap="nowrap" width="66">
        <p>O(N)</p>
      </td>
      <td nowrap="nowrap" width="66">
        <p>O(N<sup>2</sup>)</p>
      </td>
      <td nowrap="nowrap" width="66">
        <p>O(N<sup>2</sup>)</p>
      </td>
      <td nowrap="nowrap" width="84">
        <p>O(1)</p>
      </td>
      <td nowrap="nowrap" width="48">
        <p>不稳定</p>
      </td>
      <td nowrap="nowrap" width="48">
        <p>&nbsp;</p>
      </td>
      <td width="377">
        <p>&nbsp;</p>
      </td>
    </tr>
    <tr>
      <td nowrap="nowrap" width="60">
        <p>堆排序</p>
      </td>
      <td nowrap="nowrap" width="66">
        <p>O(N*log<sub>2</sub>N)</p>
      </td>
      <td nowrap="nowrap" width="66">
        <p>O(N*log<sub>2</sub>N)</p>
      </td>
      <td nowrap="nowrap" width="66">
        <p>O(N*log<sub>2</sub>N)</p>
      </td>
      <td nowrap="nowrap" width="84">
        <p>O(1)</p>
      </td>
      <td nowrap="nowrap" width="48">
        <p>不稳定</p>
      </td>
      <td nowrap="nowrap" width="48">
        <p>复杂</p>
      </td>
      <td width="377">
        <p>&nbsp;</p>
      </td>
    </tr>
    <tr>
      <td rowspan="2" nowrap="nowrap" width="55">
        <p align="center">
          <span
            style="color: rgb(0, 0, 255); --darkreader-inline-color: #337dff"
            data-darkreader-inline-color=""
            >交换</span
          >
        </p>
        <p align="center">
          <span
            style="color: rgb(0, 0, 255); --darkreader-inline-color: #337dff"
            data-darkreader-inline-color=""
            >排序</span
          >
        </p>
      </td>
      <td nowrap="nowrap" width="60">
        <p align="center">
          <span
            style="color: rgb(0, 0, 255); --darkreader-inline-color: #337dff"
            data-darkreader-inline-color=""
            >冒泡排序</span
          >
        </p>
      </td>
      <td nowrap="nowrap" width="66">
        <p>
          <span
            style="color: rgb(0, 0, 255); --darkreader-inline-color: #337dff"
            data-darkreader-inline-color=""
            >O(N)</span
          >
        </p>
      </td>
      <td nowrap="nowrap" width="66">
        <p>
          <span
            style="color: rgb(0, 0, 255); --darkreader-inline-color: #337dff"
            data-darkreader-inline-color=""
            >O(N<sup>2</sup>)</span
          >
        </p>
      </td>
      <td nowrap="nowrap" width="66">
        <p>
          <span
            style="color: rgb(0, 0, 255); --darkreader-inline-color: #337dff"
            data-darkreader-inline-color=""
            >O(N<sup>2</sup>)</span
          >
        </p>
      </td>
      <td nowrap="nowrap" width="84">
        <p>
          <span
            style="color: rgb(0, 0, 255); --darkreader-inline-color: #337dff"
            data-darkreader-inline-color=""
            >O(1)</span
          >
        </p>
      </td>
      <td nowrap="nowrap" width="48">
        <p>
          <span
            style="color: rgb(0, 0, 255); --darkreader-inline-color: #337dff"
            data-darkreader-inline-color=""
            >稳定</span
          >
        </p>
      </td>
      <td nowrap="nowrap" width="48">
        <p>
          <span
            style="color: rgb(0, 0, 255); --darkreader-inline-color: #337dff"
            data-darkreader-inline-color=""
            >简单</span
          >
        </p>
      </td>
      <td width="377">
        <p>
          1、冒泡排序是一种用时间换空间的排序方法，n小时好<br />
          2、最坏情况是把顺序的排列变成逆序，或者把逆序的数列变成顺序，最差时间复杂度O(N^2)只是表示其操作次数的数量级<br />
          3、最好的情况是数据本来就有序，复杂度为O(n)
        </p>
      </td>
    </tr>
    <tr>
      <td nowrap="nowrap" width="60">
        <p>
          <span
            style="color: rgb(0, 0, 255); --darkreader-inline-color: #337dff"
            data-darkreader-inline-color=""
            >快速排序</span
          >
        </p>
      </td>
      <td nowrap="nowrap" width="66">
        <p>
          <span
            style="color: rgb(0, 0, 255); --darkreader-inline-color: #337dff"
            data-darkreader-inline-color=""
            >O(N*log<sub>2</sub>N)</span
          >
        </p>
      </td>
      <td nowrap="nowrap" width="66">
        <p>
          <span
            style="color: rgb(0, 0, 255); --darkreader-inline-color: #337dff"
            data-darkreader-inline-color=""
            >O(N*log<sub>2</sub>N)&nbsp;</span
          >
        </p>
      </td>
      <td nowrap="nowrap" width="66">
        <p>
          <span
            style="color: rgb(0, 0, 255); --darkreader-inline-color: #337dff"
            data-darkreader-inline-color=""
            >O(N<sup>2</sup>)</span
          >
        </p>
      </td>
      <td nowrap="nowrap" width="84">
        <p>
          <span
            style="color: rgb(0, 0, 255); --darkreader-inline-color: #337dff"
            data-darkreader-inline-color=""
            >O(log<sub>2</sub>n)~O(n)&nbsp;</span
          >
        </p>
      </td>
      <td nowrap="nowrap" width="48">
        <p>
          <span
            style="color: rgb(0, 0, 255); --darkreader-inline-color: #337dff"
            data-darkreader-inline-color=""
            >不稳定</span
          >
        </p>
      </td>
      <td nowrap="nowrap" width="48">
        <p>
          <span
            style="color: rgb(0, 0, 255); --darkreader-inline-color: #337dff"
            data-darkreader-inline-color=""
            >复杂</span
          >
        </p>
      </td>
      <td width="377">
        <p>
          1、n大时好，快速排序比较占用内存，内存随n的增大而增大，但却是效率高不稳定的排序算法。<br />
          2、划分之后一边是一个，一边是n-1个，<br />
          这种极端情况的时间复杂度就是O(N^2)<br />
          3、最好的情况是每次都能均匀的划分序列，O(N*log<sub>2</sub>N)
        </p>
      </td>
    </tr>
    <tr>
      <td colspan="2" nowrap="nowrap" width="115">
        <p align="center">
          <span
            style="color: rgb(0, 0, 255); --darkreader-inline-color: #337dff"
            data-darkreader-inline-color=""
            >归并排序</span
          >
        </p>
      </td>
      <td nowrap="nowrap" width="66">
        <p>
          <span
            style="color: rgb(0, 0, 255); --darkreader-inline-color: #337dff"
            data-darkreader-inline-color=""
            >O(N*log<sub>2</sub>N)&nbsp;</span
          >
        </p>
      </td>
      <td nowrap="nowrap" width="66">
        <p>
          <span
            style="color: rgb(0, 0, 255); --darkreader-inline-color: #337dff"
            data-darkreader-inline-color=""
            >O(N*log<sub>2</sub>N)&nbsp;</span
          >
        </p>
      </td>
      <td nowrap="nowrap" width="66">
        <p>
          <span
            style="color: rgb(0, 0, 255); --darkreader-inline-color: #337dff"
            data-darkreader-inline-color=""
            >O(N*log<sub>2</sub>N)&nbsp;</span
          >
        </p>
      </td>
      <td nowrap="nowrap" width="84">
        <p>
          <span
            style="color: rgb(0, 0, 255); --darkreader-inline-color: #337dff"
            data-darkreader-inline-color=""
            >O(n)</span
          >
        </p>
      </td>
      <td nowrap="nowrap" width="48">
        <p>
          <span
            style="color: rgb(0, 0, 255); --darkreader-inline-color: #337dff"
            data-darkreader-inline-color=""
            >稳定</span
          >
        </p>
      </td>
      <td nowrap="nowrap" width="48">
        <p>
          <span
            style="color: rgb(0, 0, 255); --darkreader-inline-color: #337dff"
            data-darkreader-inline-color=""
            >复杂</span
          >
        </p>
      </td>
      <td width="377">
        <p>
          1、n大时好，归并比较占用内存，内存随n的增大而增大，但却是效率高且稳定的排序算法。
        </p>
      </td>
    </tr>
    <tr>
      <td colspan="2" nowrap="nowrap" width="115">
        <p align="center">基数排序</p>
      </td>
      <td nowrap="nowrap" width="66">
        <p>O(d(r+n))</p>
      </td>
      <td nowrap="nowrap" width="66">
        <p>O(d(r+n))</p>
      </td>
      <td nowrap="nowrap" width="66">
        <p>O(d(r+n))</p>
      </td>
      <td nowrap="nowrap" width="84">
        <p>O(rd+n)</p>
      </td>
      <td nowrap="nowrap" width="48">
        <p>稳定</p>
      </td>
      <td nowrap="nowrap" width="48">
        <p>复杂</p>
      </td>
      <td nowrap="nowrap" width="377">
        <p>&nbsp;</p>
      </td>
    </tr>
    <tr>
      <td colspan="9" nowrap="nowrap" width="870">
        <p>注：r代表关键字基数，d代表长度，n代表关键字个数</p>
      </td>
    </tr>
  </tbody>
</table>




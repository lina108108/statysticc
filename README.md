Check configuration used to specify rules on element types (BUNDLE, PACKAGE, CLASS, SOURCEFILE or METHOD) with a list of limits. Each limit applies to a certain counter (INSTRUCTION, LINE, BRANCH, COMPLEXITY, METHOD, CLASS) and defines a minimum or maximum for the corresponding value (TOTALCOUNT, COVEREDCOUNT, MISSEDCOUNT, COVEREDRATIO, MISSEDRATIO). If a limit refers to a ratio it must be in the range from 0.0 to 1.0 where the number of decimal places will also determine the precision in error messages. A limit ratio may optionally be declared as a percentage where 0.80 and 80% represent the same value.

If not specified the following defaults are assumed:

rule element: BUNDLE
limit counter: INSTRUCTION
limit value: COVEREDRATIO
This example requires an overall instruction coverage of 80% and no class must be missed:


<rules>
  <rule>
    <element>BUNDLE</element>
    <limits>
      <limit>
        <counter>INSTRUCTION</counter>
        <value>COVEREDRATIO</value>
        <minimum>0.80</minimum>
      </limit>
      <limit>
        <counter>CLASS</counter>
        <value>MISSEDCOUNT</value>
        <maximum>0</maximum>
      </limit>
    </limits>
  </rule>
</rules>
This example requires a line coverage minimum of 50% for every class except test classes:


<rules>
  <rule>
    <element>CLASS</element>
    <excludes>
      <exclude>*Test</exclude>
    </excludes>
    <limits>
      <limit>
        <counter>LINE</counter>
        <value>COVEREDRATIO</value>
        <minimum>50%</minimum>
      </limit>
    </limits>
  </rule>
</rules>

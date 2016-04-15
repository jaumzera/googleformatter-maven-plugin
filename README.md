# Google Formatter Plugin for Apache Maven

A simple [Apache Maven](http://maven.apache.org) plugin to reformat
a projects source/test-sources using the [google-java-format](https://github.com/google/google-java-format)
project.

By default the plugin will only process _stale_ source files ( comparing
against their respective `.class` files existence/timestamp ).

After processing each file, the contents `sha1` is compared against the
original and only rewritten if they no longer match.

    <plugin>
      <groupId>com.theoryinpractise</groupId>
      <artifactId>googleformatter-maven-plugin</artifactId>
      <version>1.0.3</version>
      <executions>
        <execution>
          <id>reformat-sources</id>
          <configuration>
            <includeStale>false</includeStale>
            <maxWidth>160</maxWidth>
            <sortImports>NO</sortImports>
            <javadocFormatter>NONE</javadocFormatter>
            <style>GOOGLE</style>
            <skip>false</skip>
          </configuration>
          <goals>
            <goal>format</goal>
          </goals>
          <phase>process-sources</phase>
        </execution>
      </executions>
    </plugin>

# Changes

* 1.0.3 - Fri 15 Apr 2016 20:45:58 NZST
  * Added `<skip>` ( and `-Dformatter.skip` ) configuration setting to skip reformatting code.

* 1.0.2 - Thu 14 Apr 2016 12:58:00 NZST
  * Handle missing test directories.
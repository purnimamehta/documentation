# GET courses/filter

Returns a list of courses that match specified filters.

## URL

```
https://cobalt.qas.im/api/1.0/courses/filter
```

## Parameters

<p>
  <div class="param grid-container">
    <div class="grid-20">
      <code>key</code>
      <div class="sub">required</div>
    </div>
    <div class="grid-80">
      Your unique API key.
    </div>
  </div>
</p>
- - -
<p>
  <div class="param grid-container">
    <div class="grid-20">
      <code>q</code>
      <div class="sub">required</div>
    </div>
    <div class="grid-80">
      <p>
        The filters to be applied, specified in the filter query format.
      </p>
      <p>
        Each filter within the query can be joined with either an <code>AND</code> or an <code>OR</code>.
      </p>
      <p>
        For numerical filters:
        <ul>
          <li>No operator indicates equal to (eg. <code>breadth:5</code>)</li>
          <li><code>&gt;</code> indicates greater than (eg. <code>class_size:>30</code>)</li>
          <li><code>&lt;</code> indicates less than (eg. <code>class_enrolment:>1</code>)</li>
          <li><code>&gt;=</code> indicates greater than or equal to (eg. <code>start_time:>=18</code>)</li>
          <li><code>&lt;=</code> indicates less than or equal to (eg. <code>course_level:<=200</code>)</li>
        </ul>
      </p>
      <p>
        For string filters:
        <ul>
          <li>No operator indicates contains (eg. <code>code:"CSC"</code>)</li>
          <li><code>-</code> indicates not (eg. <code>department:"-architecture"</code>)</li>
        </ul>
      </p>
      <p>
        Examples of filter combinations:
        <ul>
          <li><code>instructor:"D Liu" AND code:"CSC" AND level:<=200</code></li>
          <li><code>breadth:2 OR breadth:3</code></li>
          <li><code>prerequisites:"CSC207H1" AND code:"-MAT" OR code:"-CSC"</code></li>
        </ul>
      </p>
      <p>
        When parsing filter combinations, Cobalt allows <code>AND</code> to take precendence during logic splitting.
      </p>
      <p>
        For filters that involve properties from <code>meeting_sections</code>, an additional key is returned called <code>matched_meeting_sections</code>, which contains only the meeting sections that match the filter.
      </p>
    </div>
  </div>
</p>
- - -
<p>
  <div class="param grid-container">
    <div class="grid-20">
      <code>limit</code>
      <div class="sub">optional</div>
    </div>
    <div class="grid-80">
      The number of results to return, up to a maximum of 100 per request. The default value is 10.
    </div>
  </div>
</p>
- - -
<p>
  <div class="param grid-container">
    <div class="grid-20">
      <code>skip</code>
      <div class="sub">optional</div>
    </div>
    <div class="grid-80">
      The number of results to skip. The default value is 0.
    </div>
  </div>
</p>
- - -
<p>
  <div class="param grid-container">
    <div class="grid-20">
      <code>sort</code>
      <div class="sub">optional</div>
    </div>
    <div class="grid-80">
      <p>
        The sorting procedure to be used on the returned list. A <code>+</code> before a parameter implies ascending, and a <code>-</code> implies descending. You can also stack procedures, separating them with a space.<br />(eg. <code>+id -department</code>)
      </p>
      <p>
        The default value is <code>+id</code> (sort by id, ascending).
      </p>
    </div>
  </div>
</p>

## Example

```
https://cobalt.qas.im/api/1.0/courses/filter?q=instructor:"D Liu" AND code:"CSC" AND level:<=200
```

```json
[
  {
    "id":"CSC148H1F20159",
    "code":"CSC148H1F",
    "name":"Introduction to Computer Science",
    "description":"Abstract data types and data structures for implementing them. Linked data structures. Encapsulation and information-hiding. Object-oriented programming. Specifications. Analyzing the efficiency of programs. Recursion. This course assumes programming experience as provided by CSC108H1. Students who already have this background may consult the Computer Science Undergraduate Office for advice about skipping CSC108H1. Practical (P) sections consist of supervised work in the computing laboratory. These sections are offered when facilities are available, and attendance is required. NOTE: Students may go to their college to drop down from CSC148H1 to CSC108H1. See above for the drop down deadline.",
    "division":"Faculty of Arts and Science",
    "department":"Computer Science",
    "prerequisites":"CSC108H1/(equivalent programming experience)",
    "exclusions":"CSC150H1; you may not take this course after taking more than two CSC courses at the 200-level or higher",
    "level":100,
    "campus":"UTSG",
    "term":"2015 Fall",
    "breadths":[
      5
    ],
    "meeting_sections":[
      {
        "code":"L0101",
        "instructors":[
          "D Liu"
        ],
        "times":[
          {
            "day":"MONDAY",
            "start":10,
            "end":11,
            "duration":1,
            "location":"RW 110"
          },
          {
            "day":"WEDNESDAY",
            "start":10,
            "end":11,
            "duration":1,
            "location":"RW 110"
          },
          {
            "day":"FRIDAY",
            "start":10,
            "end":11,
            "duration":1,
            "location":"RW 110"
          }
        ],
        "size":156,
        "enrolment":0
      },
      {
        "code":"L0201",
        "instructors":[
          "D Liu"
        ],
        "times":[
          {
            "day":"MONDAY",
            "start":14,
            "end":15,
            "duration":1,
            "location":"RW 117"
          },
          {
            "day":"WEDNESDAY",
            "start":14,
            "end":15,
            "duration":1,
            "location":"RW 117"
          },
          {
            "day":"FRIDAY",
            "start":14,
            "end":15,
            "duration":1,
            "location":"RW 117"
          }
        ],
        "size":156,
        "enrolment":0
      },
      {
        "code":"T0101",
        "instructors":[

        ],
        "times":[
          {
            "day":"THURSDAY",
            "start":9,
            "end":11,
            "duration":2,
            "location":""
          }
        ],
        "size":108,
        "enrolment":0
      },
      {
        "code":"T0201",
        "instructors":[

        ],
        "times":[
          {
            "day":"THURSDAY",
            "start":11,
            "end":13,
            "duration":2,
            "location":""
          }
        ],
        "size":108,
        "enrolment":0
      },
      {
        "code":"T5101",
        "instructors":[

        ],
        "times":[
          {
            "day":"THURSDAY",
            "start":19,
            "end":21,
            "duration":2,
            "location":""
          }
        ],
        "size":72,
        "enrolment":0
      },
      {
        "code":"T0301",
        "instructors":[

        ],
        "times":[
          {
            "day":"THURSDAY",
            "start":13,
            "end":15,
            "duration":2,
            "location":""
          }
        ],
        "size":36,
        "enrolment":0
      }
    ],
    "matched_meeting_sections":[
      {
        "code":"L0101",
        "instructors":[
          "D Liu"
        ],
        "times":[
          {
            "day":"MONDAY",
            "start":10,
            "end":11,
            "duration":1,
            "location":"RW 110"
          },
          {
            "day":"WEDNESDAY",
            "start":10,
            "end":11,
            "duration":1,
            "location":"RW 110"
          },
          {
            "day":"FRIDAY",
            "start":10,
            "end":11,
            "duration":1,
            "location":"RW 110"
          }
        ],
        "size":156,
        "enrolment":0
      },
      {
        "code":"L0201",
        "instructors":[
          "D Liu"
        ],
        "times":[
          {
            "day":"MONDAY",
            "start":14,
            "end":15,
            "duration":1,
            "location":"RW 117"
          },
          {
            "day":"WEDNESDAY",
            "start":14,
            "end":15,
            "duration":1,
            "location":"RW 117"
          },
          {
            "day":"FRIDAY",
            "start":14,
            "end":15,
            "duration":1,
            "location":"RW 117"
          }
        ],
        "size":156,
        "enrolment":0
      }
    ]
  },
  {
    "id":"CSC209H1S20161",
    "code":"CSC209H1S",
    "name":"Software Tools and Systems Programming",
    "description":"Software techniques in a Unix-style environment, using scripting languages and a machine-oriented programming language (typically C). What goes on in the operating system when programs are executed. Core topics: creating and using software tools, pipes and filters, file processing, shell programming, processes, system calls, signals, basic network programming.",
    "division":"Faculty of Arts and Science",
    "department":"Computer Science",
    "prerequisites":"CSC207H1",
    "exclusions":"CSC372H1, CSC369H1, CSC469H1",
    "level":200,
    "campus":"UTSG",
    "term":"2016 Winter",
    "breadths":[
      5
    ],
    "meeting_sections":[
      {
        "code":"L0101",
        "instructors":[
          "M Craig"
        ],
        "times":[
          {
            "day":"MONDAY",
            "start":12,
            "end":13,
            "duration":1,
            "location":"RW 110"
          },
          {
            "day":"WEDNESDAY",
            "start":12,
            "end":13,
            "duration":1,
            "location":"RW 110"
          }
        ],
        "size":146,
        "enrolment":0
      },
      {
        "code":"L0201",
        "instructors":[
          "D Liu"
        ],
        "times":[
          {
            "day":"MONDAY",
            "start":10,
            "end":11,
            "duration":1,
            "location":"LM 161"
          },
          {
            "day":"WEDNESDAY",
            "start":10,
            "end":11,
            "duration":1,
            "location":"LM 161"
          }
        ],
        "size":140,
        "enrolment":0
      },
      {
        "code":"L5101",
        "instructors":[
          "M Craig"
        ],
        "times":[
          {
            "day":"WEDNESDAY",
            "start":18,
            "end":20,
            "duration":2,
            "location":"LM 162"
          }
        ],
        "size":146,
        "enrolment":0
      },
      {
        "code":"T0101",
        "instructors":[

        ],
        "times":[
          {
            "day":"FRIDAY",
            "start":13,
            "end":14,
            "duration":1,
            "location":""
          }
        ],
        "size":96,
        "enrolment":0
      },
      {
        "code":"T0201",
        "instructors":[

        ],
        "times":[
          {
            "day":"FRIDAY",
            "start":14,
            "end":15,
            "duration":1,
            "location":""
          }
        ],
        "size":96,
        "enrolment":0
      },
      {
        "code":"T0301",
        "instructors":[

        ],
        "times":[
          {
            "day":"FRIDAY",
            "start":15,
            "end":16,
            "duration":1,
            "location":""
          }
        ],
        "size":96,
        "enrolment":0
      },
      {
        "code":"T5101",
        "instructors":[

        ],
        "times":[
          {
            "day":"WEDNESDAY",
            "start":20,
            "end":21,
            "duration":1,
            "location":""
          }
        ],
        "size":96,
        "enrolment":0
      }
    ],
    "matched_meeting_sections":[
      {
        "code":"L0201",
        "instructors":[
          "D Liu"
        ],
        "times":[
          {
            "day":"MONDAY",
            "start":10,
            "end":11,
            "duration":1,
            "location":"LM 161"
          },
          {
            "day":"WEDNESDAY",
            "start":10,
            "end":11,
            "duration":1,
            "location":"LM 161"
          }
        ],
        "size":140,
        "enrolment":0
      }
    ]
  }
]
```
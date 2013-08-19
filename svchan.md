# Satellite Channel Structure

## Background
All defined satellites have a structure used to pass information between acquisition and tracking channel on hardware.
This structure defined the information for acquisition/tracking channel to search/lock the signal in the real-time.


## Signal Structure
```c
struct sv_signal
{
  struct list_head  list;
};
```

## Major Channel Structure


```c
struct sv_search
{
  const struct acq_time_para  *search_param;  // Pointer to acquisition search parameters
  int                         acqmode;        // Acquisition mode
};

struct sv_channel
{
  struct sv_signal  sig;
  int               search_quality; // Satellite tracking status
  struct sv_search  *search_config;
};
```


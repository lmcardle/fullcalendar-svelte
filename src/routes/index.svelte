<script>
	import { onMount } from 'svelte';
	import { Calendar } from '@fullcalendar/core';
	import { browser } from '$app/env';

	let calendar;
	let calendarComponentRef;

	let options = {
		initialView: 'dayGridMonth',
		dateClick: (eventInfo) => {
			console.log('date clicked', eventInfo);
		},
		dayMaxEvents: true,
		eventClick: (eventInfo) => {
			console.log('event clicked', eventInfo);
		},
		events: [
			{
				id: 1,
				title: 'All Day Event',
				description: '',
				allDay: true,
				start: '2021-10-01',
				end: null,
				groupId: null,
				repeatFrequency: null,
				endRepeatDate: null
			},
			{
				id: 2,
				title: 'Long Event',
				description: '',
				allDay: true,
				start: '2021-10-07',
				end: '2021-10-10',
				groupId: null,
				repeatFrequency: null,
				endRepeatDate: null
			},
			{
				id: 3,
				title: 'Repeating Event',
				description: '',
				allDay: false,
				start: '2021-10-09T16:00:00+00:00',
				end: null,
				groupId: '999',
				repeatFrequency: null,
				endRepeatDate: null
			},
			{
				id: 4,
				title: 'Repeating Event',
				description: '',
				allDay: false,
				start: '2021-10-16T16:00:00+00:00',
				end: null,
				groupId: '999',
				repeatFrequency: null,
				endRepeatDate: null
			},
			{
				id: 5,
				title: 'Conference',
				description: '',
				allDay: true,
				start: '2021-10-02',
				end: '2021-10-04',
				groupId: null,
				repeatFrequency: null,
				endRepeatDate: null
			},
			{
				id: 6,
				title: 'Meeting',
				description: '',
				allDay: false,
				start: '2021-10-03T10:30:00+00:00',
				end: '2021-10-03T12:30:00+00:00',
				groupId: null,
				repeatFrequency: null,
				endRepeatDate: null
			},
			{
				id: 7,
				title: 'Lunch',
				description: '',
				allDay: false,
				start: '2021-10-03T12:00:00+00:00',
				end: null,
				groupId: null,
				repeatFrequency: null,
				endRepeatDate: null
			},
			{
				id: 8,
				title: 'Birthday Party',
				description: '',
				allDay: false,
				start: '2021-10-04T07:00:00+00:00',
				end: null,
				groupId: null,
				repeatFrequency: null,
				endRepeatDate: null
			},
			{
				id: 9,
				url: 'http://google.com/',
				title: 'Click for Google',
				description: '',
				allDay: true,
				start: '2021-10-28',
				end: null,
				groupId: null,
				repeatFrequency: null,
				endRepeatDate: null
			},
			{
				id: 10,
				title: 'Meeting',
				description: '',
				allDay: false,
				start: '2021-10-03T14:30:00+00:00',
				end: null,
				groupId: null,
				repeatFrequency: null,
				endRepeatDate: null
			},
			{
				id: 11,
				title: 'Happy Hour',
				description: '',
				allDay: false,
				start: '2021-10-03T17:30:00+00:00',
				end: null,
				groupId: null,
				repeatFrequency: null,
				endRepeatDate: null
			},
			{
				id: 12,
				title: 'Dinner',
				description: '',
				allDay: false,
				start: '2021-10-03T20:00:00+00:00',
				end: null,
				groupId: null,
				repeatFrequency: null,
				endRepeatDate: null
			}
		]
	};

	if (browser) {
		onMount(async () => {
			await import('@fullcalendar/core/vdom');
			options.plugins = [(await import('@fullcalendar/daygrid')).default];
			options = { ...options };

			calendar = new Calendar(calendarComponentRef, { ...options });
			calendar.render();

			return () => {
				calendar && calendar.destroy();
			};
		});
	}
</script>

<div bind:this={calendarComponentRef} />
